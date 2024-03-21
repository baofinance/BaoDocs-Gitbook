# Liquidity Balancers

Bao Finance has deployed an AMM-based Liquidity Balancer that mints and burns synths directly into liquidity pools to sustainably align incentives.

### How It Works

Liquidity Balancers have the capability to:

* **Mint** baoUSD and baoETH stablecoins directly into paired liquidity pools
* **Burn** baoUSD and baoETH synths from pools when redeemed

### Key Benefits

* **Earn trading fees** through providing baoUSD or baoETH liquidity the protocol will eanr trading fees
* **Maintain synth pegs** via pool rebalancing. When a synth is below peg the balancer will withdraw and burn, bringing back the balance to a healthy level. When the synth is above peg the balancer will mint tokens to the liquidity pool to bring back the balance of the pool
* **Liquidity rewards** are earned by the LP tokens the Balancer owns while it has tokens minted in the pool. &#x20;

### Initial Deployment

The Liquidity Balancer launched using Balancer pools for baoUSD and baoETH against their underlying collateral assets.&#x20;
