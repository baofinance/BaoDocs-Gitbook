# How they work

## Issue

When minting new basket tokens, the deposited token is used to buy the underlying assets, which are deposited in yield farms then the yield-bearing tokens from those farms are deposited into a vault.&#x20;

The issue command asks for a larger deposit than is needed to buy the underlying tokens, to allow for price slippage. Any unused ETH is returned to your wallet.\
\
As yield is farmed and prices change on underlying assets, the cost of each nest token will change to reflect the performance of the underlying tokens.

## Redeem

When you redeem, the share of underlying tokens represented by the basket tokens you are redeeming will be returned to your wallet, or sold for your redemption token of choice then returned to your wallet depending on which redeem option you choose.

## Price

Baskets backed by the underlying tokens.\
\
Any time the price diverges on an exchange from that of the combined price of the underlying tokens it creates an arbitrage opportunity.&#x20;

When the nest price is above the underlying assets, you can issue more of the nest (which buys the underlying assets) and then sell the nest tokens for a profit.&#x20;

When the nest price is below that of the underlying tokens, you can buy nest tokens and redeem them for the underlying assets then sell them for a profit.
