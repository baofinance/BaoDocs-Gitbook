# Liquidity Balancers

Liquidity Balancers are pivotal in maintaining a stable peg and generating revenue. They achieve this by minting and burning synths directly into liquidity pools, ensuring a solid peg and creating income from arbitrage and trading fees.

Only pools containing backing assets can have a liquidity balancer. This ensures that synths are backed only by approved collaterals, providing a secure and reliable system that you can confidently participate in.

### How It Works

Liquidity Balancers have the capability to:

* **Mint** baoUSD and baoETH stablecoins directly into paired liquidity pools containing backing assets, receiving LP tokens in return.
* **Burn** baoUSD and baoETH synths from pools when redeeming LP tokens.

An example of how it works:

* baoUSD is trading at 1.01, due to a baoUSD/LUSD liquidity pool balance of 100 baoUSD/ 500 LUSD.
* The baoUSD liquidity balancer mints 400 baoUSD into the liquidity pool, bringing the balance back to 50:50, with 500 baoUSD and 500 LUSD in the pool.
* The liquidity balancer returns 404 LP tokens, representing a small unrealized profit due to adding synths 1% above their fair value.
* Later, the baoUSD/LUSD liquidity pool became unbalanced again, with baoUSD trading at 0.99 due to a pool balance of 100 LUSD and 500 baoUSD.
* The liquidity balancer redeems 396 LP tokens, receives 400 baoUSD, and burns them.
* The liquidity balancer now owns 8 LP tokens, which can remain as protocol-owned liquidity or be redeemed as revenue.
