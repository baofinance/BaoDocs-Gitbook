---
description: Decentralized, fully backed, firmly pegged, and capital efficient.
---

# baoUSD and baoETH

Bao's vision for its on-chain derivatives is to provide the most secure decentralized pegged tokens possible. We recognize that trust is essential for liquidity providers and protocol users, so we ensure we meet the highest standards every step of the way.

### Backing

A pegged token is only as good as its weakest collateral. ETH is the only token guaranteed to always have liquidity on Ethereum. With that in mind, the community has chosen only to allow ETH and ETH-backed tokens with the highest decentralization standards and can unwind fully. An excellent example is an ETH LST (Liquid Staking Token) that enabled withdrawals, enabling all liquidity to exit to ETH if required. This approach reduces the chance of risk mismanagement or market manipulation leading to bad debt on the protocol. Approved backing assets are:

* ETH
* wstETH
* rETH
* LUSD

**Backing Mechanisms**

There are three different ways that on-chain derivatives can be created (and backed).

1. **Collateralized Debt Positions.** Approved collateral is deposited into Bao Borrow Vaults, allowing you to borrow up to 90% of its value as baoUSD or baoETH. Suppose the collateral value drops compared to the loan position and is worth less than 90% of the loan. In that case, your position will get flagged for liquidation. The loan will be repaid, and collateral will be claimed. A bonus is taken from the difference between the collateral and loan values to incentivize repayment and suppliment a reserve fund.  Anyone can liquidate a position, but these actions are usually carried out by bots, who monitor lending protocols for profitable liquidation opportunities. Users with a collateralized debt position should ensure their health ratio stays above 1 to avoid liquidation and therefore pay incentives to liquidators from their collateral. We keep on-chain derivatives fully backed by liquidating positions with a bad health ratio.
2. **The Minter (coming soon)** allows users to swap collateral tokens for on-chain derivatives with 100% collateral efficiency. It acts like a single collateralized debt position by tokenizing the liabilities (stable token) and the difference between the debt and collateral value (leverage token). You can read more about the upcoming Minter here.
3. **Liquidity Balancers.** Our liquidity balancer contracts can mint and burn on-chain derivatives directly into/from liquidity pools containing backing assets. They mint tokens when on-chain derivatives are above the peg and then burn them again if they are below the peg. The liquidity balancer ensures a strong peg. Pools with backing assets, like baoUSD/LUSD, can have Liquidity Balancers, meaning each token removed from a liquidity pool is swapped for a backing asset, maintaining protocol solvency. You can read more about our Liquidity Balancers [here](liquidity-balancers.md).

### The Peg

baoUSD has been live for over a year and has remained well pegged throughout its history. As liquidity grows, the peg strengthens further, as trading activity requires less frequent rebalances by the Liquidity Balancers. baoETH has a similar history of maintaining a peg, even during periods of high volatility.

Maintaining a solid peg is essential for us.&#x20;

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://www.dextools.io/app/en/ether/pair-explorer/0x7e9afd25f5ec0eb24d7d4b089ae7ecb9651c8b1f-0x5f98805a4e8be255a32880fdec7f6728c6568ba0-0x7945b0a6674b175695e5d1d08ae1e6f13744abb0?t=1722699150201">https://www.dextools.io/app/en/ether/pair-explorer/0x7e9afd25f5ec0eb24d7d4b089ae7ecb9651c8b1f-0x5f98805a4e8be255a32880fdec7f6728c6568ba0-0x7945b0a6674b175695e5d1d08ae1e6f13744abb0?t=1722699150201</a></p></figcaption></figure>

Various battle-tested mechanisms keep a robust peg.

* **Variable borrow rates.** Our Borrow vaults have variable borrow rates, meaning if there is a strain on the pegging mechanisms on the low side of the peg, interest rates will increase, incentivizing the repurchasing of borrowed tokens to repay loans. Interest rates are affected by the number of tokens available to borrow. Decreasing available borrow tokens increases the interest rates, and vice versa.
* **Liquidity Balancers.** When pegged tokens are trading above their fair value, Liquidity Balancers contracts mint pegged tokens directly into liquidity pools containing backing assets. Minting into and burning from liquidity pools directly affects the price, bringing the peg back instantly. At a later date, if required, the Liquidity Balancer can redeem minted tokens from the liquidity pool to instantly increase the price of the pegged tokens.
* **Redeemability (coming soon with the Minter).** The Minter allows pegged tokens (and variable leverage tokens) to be minted or redeemed for backing assets at a 1:1 rate (before fees).

### **Decentralization**

One of the main benefits of cryptocurrencies is the ability to decentralize and remove trust. While there are some centralized aspects at the beginning, with multi-sigs controlling various parameters like the borrow limits (and interest rates), we are actively working on removing trust and will not stop until the protocol is completely trustless.
