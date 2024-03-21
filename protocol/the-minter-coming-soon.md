---
description: >-
  Documentation for The Minter is a work-in-progress as features are under
  active development. Details are subject to change.
---

# The Minter (Coming soon)

The Minter introduces an innovative approach to minting tokens - splitting the value of collateral between stable and leverage tokens. After the initial market is created, anyone can deposit the collateral token and swap it for either the stable or leverage token. Holding both in proportion to the initial market creation is the same as holding the collateral token.\
\
For example, if ETH was accepted to mint baoUSD (the stable) and levETH (the leverage token), you could hold both and it would be the same as holding ETH.&#x20;

### First Implementation

The initial deployment utilizes ETH to mint baoUSD and levETH:

The system is designed for 100% capital efficiency, with both tokens redeemable for the backing ETH collateral.

### Stability Mechanisms

To ensure the system remains fully collateralized there are 2 stability mechanisms.

* Stability Pools: Accepts stable tokens and earns yield from collateral while idle. When the value of collateral falls to a set level, stable tokens in the liquidity pool are burned and replaced with collateral or leverage tokens.
* Variable Fees: Adjusted algorithmically to support a healthy collateralization ratio.

### Future Implementations

The goal is to expand The Minter to enable stablecoins linked to any data feed and their counterpart leverage tokens. As long as there is demand for both sides of the market and a data feed, there really is no limits to the tokens that can be created. Check out the [Synthetics Use Cases](../synth-use-cases.md) page to see some examples. \
\
veBAO holders will vote for which markets to create initially, and the end game is to create a marketplace allowing anyone to create their own markets.
