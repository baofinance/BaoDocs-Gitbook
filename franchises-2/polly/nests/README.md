# Nests

Nests are a single token that represents ownership of a basket of underlying tokens. The underlying assets are managed by a vault, which can put them to work yield farming in various protocols.

## Issue or Swap?

Depending on the market conditions, it is sometimes better to issue nDEFI and other times it is better to buy it on SushiSwap. The nDEFI nest page has all the information you need to help you make your decision.

![](<../../../.gitbook/assets/image (59).png>)

* (A) - The price of nDEFI tokens on SushiSwap
* (B) - The combined price of underlying tokens making up 1 nDEFI on SushiSwap
* (C) - The combined price of underlying tokens making up 1nDEFI on main net. This is shown to let you see if you are paying a premium for assets by minting nDEFI, which buys the underlying tokens on polygon. If there is a large difference it may be better to wait for the prices to converge or you may choose to arbitrage the polygon markets with the main net ones.
* (D) - The premium for buying nDEFI tokens on SushiSwap vs minting them.

## How they work

### Issue

If you have ETH in your wallet on the polygon network, you can use it to mint new nest tokens. When minting new nests the ETH is used to buy the underlying assets, which are deposited in yield farms then the yield-bearing tokens from those farms are deposited into a vault. A small [**entrance fee**](../fees.md) \*\*\*\* is also taken from the ETH to buy Polly and send it to the burn address.

The issue command asks for more ETH than is needed to buy the required Polly and underlying tokens to allow for price slippage then any unused ETH is returned to your wallet.\
\
As yield is farmed and prices change on underlying assets, the cost of each nest token will change to reflect the performance of the underlying tokens.

![](https://documents.lucid.app/documents/19a03ab9-9cd3-4ed3-87fd-e2a87dbcd487/pages/0\_0?a=639\&x=5\&y=139\&w=1650\&h=902\&store=1\&accept=image%2F\*\&auth=LCA%2012afa61013c357ed20cd951af0f2ba6ababb69f9-ts%3D1632762987)

### Redeem

When you redeem, the share of underlying tokens represented by the nest you are redeeming will be returned to your wallet, or sold for ETH on Sushi Swap then returned to your wallet depending on which redeem option you choose.

### Price

Nest prices are fundamentally linked to the price of the underlying tokens and the yield gained on them from yield farming. Any time the price diverges in the SushiSwap pool from that of the combined price of the underlying tokens it creates an arbitrage opportunity.

When the nest price is above the underlying assets, you can issue more of the nest (which buys the underlying assets) and then sell the nest tokens for a profit.

When the nest price is below that of the underlying tokens, you can buy nest tokens from SushiSwap and redeem them for the underlying assets then sell them for a profit.

### Yield Farming and reflexive fees

Over time each nest token will be worth more and more underlying tokens as they are deposited into yield farms and compounded. Also, every time someone redeems nest tokens part of the [**exit fee**](../fees.md) is used to reward current holders of the nest, by giving the wallet redeeming slightly less of the underlying tokens. This means that each nest token now represents slightly more of each underlying token.
