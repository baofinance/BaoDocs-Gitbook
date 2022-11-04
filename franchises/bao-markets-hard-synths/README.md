# Bao Markets (hard synths)

Bao starts its journey towards an open and accurate financial marketplace with BAO Markets, our minimum viable synth product.&#x20;

Bao Markets allows you to use different collateral types to mint synthetic tokens, starting with Bao USD.

They **** are built upon the [Compound ](https://compound.finance/)protocol and therefore share many similar functions and components.&#x20;

If you are not familiar with the Compound protocol, we recommend reading through their [documentation](https://compound.finance/docs) which is extensive and well structured.     &#x20;

[Inverse Finance](https://www.inverse.finance/) expanded this protocol by introducing the **Fed** as an additional actor. The **Fed** is a smart contract (controlled by a multisig) that is able to mint ERC20 tokens and deposit them directly into the protocol. These ERC20 tokens can now be borrowed, with collateral that has been deposited into the protocol. In order to determine how many of the ERC20 tokens users can borrow, a price needs to be established. This is done via an **Oracle** contract that contains a mapping from the ERC20 token to a chainlink price feed. It is a smooth way to turn compound token lending system into a system for minting synthetic tokens.&#x20;

## Bao USD

baoUSD allows any user access to a dollar-pegged token and to be their own bank. You can take out or repay loans in seconds, without any approvals or credit checks.&#x20;

baoUSD is backed by locked collateral tokens and there are multiple mechanisms helping it keep its peg. Its supply is controlled by "the fed".

Below we will explore the various pegging mechanisms, which all work together to help Bao USD stay as close to its peg as possible.

### Ballast

Ballast allows users to mint baoUSD with DAI or redeem deposited DAI with baoUSD. The mint and redeem fee is set to 1%, which means the price of baoUSD should fluctuate between $0.99 and $1.01. Any time the price is above or below this price represents an opportunity for low-risk arbitrage between the ballast and the market selling outside of these prices.

This allows users to repay their loans at close to $1 even if the price of baoUSD deviates from the peg on exchanges.&#x20;

### Loan Arbitrage

When the price of baoUSD is >$1 there will be an incentive to take out a new loan position and sell it at a premium. When the price of baoUSD is below <$1 there is an incentive to buy baoUSD for a discount and pay off loans.

### Supply

The supply of baoUSD can be contracted or expanded which will in turn increase or decrease the interest rates for borrowing or lending Bao USD&#x20;

If the price of baoUSD is below its peg, the supply of baoUSD can be contracted, increasing the interest rate on all loans in the system. \
\
This will help to increase buy pressure as the incentive to pay back a loan is increased, or from people who want to take advantage of the inflated interest rate by buying Bao USD and lending it. The opposite can of course be done if the price is above peg.

## Liquidations

Liquidations are vital for the safety of the protocol.&#x20;

To ensure that no borrow position is ever under-collateralized anyone has the ability to repay another user's borrow if the borrowed value has exceeded their borrow limit.

As liquidations have to be performed in a timely manner, a share of the borrower's collateral will be transferred to the user that liquidated/repaid the borrower's position.&#x20;

The Liquidation Incentive dictates what percent of the repaid amount is seized as a reward to the liquidator.

&#x20;Liquidation Incentive: 10%

&#x20;In order to increase the security of the protocol in this early stage, a percentage of the liquidation reward goes to the protocol reserves.&#x20;

Protocol Share: 2.8%&#x20;

Real Liquidator Incentive: 7.2%

## IMF

The Initial Margin Factor (IMF) is independently set for each bdAsset and influences the ratio at which the value of borrowed assets has to be covered by collateral.

As an example: We have deposited USDC as collateral into the protocol. We now want to use our USDC in order to borrow bUSD. If a collateral type has a default collateral factor of 0.9 it means that users can use 90% of deposited collateral to borrow bUSD. For most users that knowledge will be sufficient.&#x20;

For users with larger deposits (we are talking of valuations +$1,000,000) a high collateral factor such as 90% poses a higher risk to the protocol. In order to prevent volatile markets or slow liquidators causing insolvency of the protocol (and the user), we decrease the relative borrowing power with an increase in collateral value.&#x20;

The IMF dictates how steep the drop in borrowing power is with an increase in collateral value.

![An arbitrary example of how the IMF influences the borrowing power in comparison to a static collateral factor of 85%.](<../../.gitbook/assets/image (92).png>)

The IMF is calculated with the following formula:

$$
Collateral Factor = size * price * min(MaxCollateralFactor, 1.1 / (1+IMF * \sqrt{size})
$$

The implementation in the comptroller.sol contract:

```
    function getHypotheticalAccountLiquidityInternal(
    address account,
    CToken cTokenModify,
    uint redeemTokens,
    uint borrowAmount)
    internal view returns (Error, uint, uint) {
    
    AccountLiquidityLocalVars memory vars; // Holds all our calculation results
    uint oErr;

    // For each asset the account is in
    CToken[] memory assets = accountAssets[account];
    for (uint i = 0; i < assets.length; i++) {
        CToken asset = assets[i];

        // Read the balances and exchange rate from the cToken
        (oErr, vars.cTokenBalance, vars.borrowBalance, vars.exchangeRateMantissa) = asset.getAccountSnapshot(account);
        if (oErr != 0) { // semi-opaque error code, we assume NO_ERROR == 0 is invariant between upgrades
            return (Error.SNAPSHOT_ERROR, 0, 0);
        }
        vars.collateralFactor = Exp({mantissa: markets[address(asset)].collateralFactorMantissa});
		vars.imfFactor = Exp({mantissa: markets[address(asset)].imfFactorMantissa});
        vars.exchangeRate = Exp({mantissa: vars.exchangeRateMantissa});

        // Get the normalized price of the asset
        vars.oraclePriceMantissa = oracle.getUnderlyingPrice(asset);
        
        if (vars.oraclePriceMantissa == 0) {
            return (Error.PRICE_ERROR, 0, 0);
        }
        
        vars.oraclePrice = Exp({mantissa: vars.oraclePriceMantissa});
		
	vars.precomputeTokens = mul_ScalarTruncate(vars.exchangeRate, vars.cTokenBalance);
		
	vars.postIMFSize = mul_ScalarTruncate(vars.imfFactor, sqrt(vars.precomputeTokens));
		
	vars.modCollateralFactor = mul_ScalarTruncate(vars.collateralFactor, 1e18);

	vars.preMinDenum = (1000000000000000000 + mul_(1000000000, vars.postIMFSize));

	vars.preMinEnum = 1100000000000000000;
		
	vars.preMin = div_(mul_(vars.preMinEnum, 1e18), vars.preMinDenum);

	vars.getMin = min(vars.modCollateralFactor, vars.preMin);
		
	//convertGetMin to Exp
	vars.convertedGetMin = Exp({mantissa: vars.getMin});
        
        // Pre-compute a conversion factor from tokens -> ether (normalized price value)
        vars.tokensToDenom = mul_(mul_(vars.convertedGetMin, vars.exchangeRate), vars.oraclePrice);

        // sumCollateral += tokensToDenom * cTokenBalance
        vars.sumCollateral = mul_ScalarTruncateAddUInt(vars.tokensToDenom, vars.cTokenBalance, vars.sumCollateral);
        
        // sumBorrowPlusEffects += oraclePrice * borrowBalance
        vars.sumBorrowPlusEffects = mul_ScalarTruncateAddUInt(vars.oraclePrice, vars.borrowBalance, vars.sumBorrowPlusEffects);

        // Calculate effects of interacting with cTokenModify
        if (asset == cTokenModify) {
            // redeem effect
            // sumBorrowPlusEffects += tokensToDenom * redeemTokens
            vars.sumBorrowPlusEffects = mul_ScalarTruncateAddUInt(vars.tokensToDenom, redeemTokens, vars.sumBorrowPlusEffects);

            // borrow effect
            // sumBorrowPlusEffects += oraclePrice * borrowAmount
            vars.sumBorrowPlusEffects = mul_ScalarTruncateAddUInt(vars.oraclePrice, borrowAmount, vars.sumBorrowPlusEffects);
        }
    }

    // These are safe, as the underflow condition is checked first
    if (vars.sumCollateral > vars.sumBorrowPlusEffects) {
        return (Error.NO_ERROR, vars.sumCollateral - vars.sumBorrowPlusEffects, 0);
    } else {
        return (Error.NO_ERROR, 0, vars.sumBorrowPlusEffects - vars.sumCollateral);
    }
}
```



##

