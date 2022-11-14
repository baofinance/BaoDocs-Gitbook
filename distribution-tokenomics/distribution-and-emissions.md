# Distribution and Emissions

## Phase #1 - Community Distribution (COMPLETED November 21, 2022):

During the community distribution phase, users earned Bao rewards each block for staking their LP tokens on the Bao Farming page.

During these two years, around 1.09 Trillion bao were distributed. 95% of rewards were locked, and 5% were liquid. These Bao tokens were distributed using the bao yield farming page on bao.finance, based on the SushiSwap MasterChef protocol.\
\
The locked portion of tokens will be distributed in Phase 2.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## Phase #2 - BAOv2 and veBAO (November 25, 2022, onwards)

{% hint style="info" %}
To enter stage 2 and implement veBAO, a token migration was required, primarily because the token supply was too high to be compatible with the veBAO contracts.&#x20;

As a result, the BAOv2 token supply is 1000x smaller, and BAOv1 can swap their BAO tokens to BAOv2 at a ratio of 1000:1
{% endhint %}

### BAOv2 new emissions schedule

_**Initial Supply of BAOv2** = (total locked BAOv1 tokens across main-net and xDAI) / 1000 + (all circulating BAOv1 across main-net and xDAI) / 1000 **= 1.09 Billion BAOv2 Tokens**_

The BAOv2 initial supply matches the supply of Baov1 tokens on all networks, including locked tokens, reduced by a factor of 1000.&#x20;

The initial supply represents a % (initial rate) of the total supply. The initial rate is 43%, similar to Curve Finance, who distributed 43% of all the CRV tokens that will ever be minted to the initial supply of the token. \
\
This leaves 57% of the maximum supply minted over time to the LP tokens staked in liquidity gauges.

Emissions function to determine circulating supply over time:

![](https://global.discourse-cdn.com/standard10/uploads/bao/original/1X/fe714c6a9fce1f7d6570c01e568bf3d50e2716e9.png)

As time moves forward beyond the starting point of the new token, each year, the slope will reduce the supply emissions rate by 2^(¼) based on the function of the current emissions. This means over time, less and less BAOv2 supply emissions will be given out to LPs staked in gauges as it is with curve finance’s model.
