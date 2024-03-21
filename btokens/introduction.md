# Introduction

## bTokens

bTokens are ERC20 tokens that represent balances supplied to Bao Finance lending markets. They enable simplified interactions while accruing interest and ownership rights.

### Overview

Each asset integrated into Bao Finance has an associated bToken contract. bTokens provide:

* Interest accrual on supplied asset balances
* Collateralization for borrowing other assets
* Transferability between addresses

bTokens are the primary means of interacting with Bao Finance for activities like:

* Supplying and withdrawing assets
* Borrowing against collateral
* Making repayments
* Liquidating underwater positions
* Transferring balances

### How bTokens Earn Interest

Each lending market has its own supply interest rate (APR) that accrues through the bToken exchange rate.

As the exchange rate increases over time, each bToken becomes convertible into a higher amount of the underlying asset. This is how interest is earned.

For example, supplying 1000 ETH when exchange rate is 0.02 would mint 49,825 bETH. After a few months at a 0.021591 rate, those same 49,825 bETH could withdraw 1075.78 ETH.

Even as the exchange rate rises, your bToken balance remains the same. Interest accrues through the rate, not distributions.

### Viewing bToken Balances

Each bToken contract is viewable on Etherscan. bToken balances also show in wallet token lists.

### Transferring bTokens

bTokens are freely transferable to other addresses. But caution is warranted - transferring bTokens shifts your deposited balance of that asset within Bao Finance to the recipient.

If you send bTokens to a friend, your deposited balance declines and theirs increases by that amount. Transfers will fail if it would cause negative liquidity.

### Risks

While bTokens simplify Bao Finance interactions, they carry inherent risks to consider:

* Transferring bTokens shifts deposited balances between users; be cautious when sending.
* Smart contract risks could lead to loss of supplied assets.
