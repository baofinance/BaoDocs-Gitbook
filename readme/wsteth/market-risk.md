# Market Risk

Analyzing market risks for liquid staked ETH like wstETH as collateral is vital for understanding its market dynamics, adoption, and financial health. It provides a data-driven basis for informed decision-making, crucial in navigating the DeFi ecosystem's uncertainties.

## Peg Performance

stETH has seen around an 8% depeg incident during mid 2022 due to heavy market selling and did not fully recover until the end of Q1 2023. During this incident, staked ETH could not be withdrawn. Staked ETH has been withdrawable since April 2023 and the peg has been much more resilient since. Future market volatility should have a shorter lasting effect on the peg due to the mechanisms allowing the redemption of stETH in exchange for ETH.

<figure><img src="../../.gitbook/assets/Untitled (1).png" alt=""><figcaption><p>source: <a href="https://www.coingecko.com/en/coins/lido-staked-ether">coingecko</a></p></figcaption></figure>

Price impact over the 30 days has largely been minimal, with occasional transactions having larger impacts on price

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>source: <a href="https://dune.com/lido/wsteth-price-impact">lido dune</a></p></figcaption></figure>

Price impact by swap size shows that larger swaps are able to transact with minimal impact, indicating the swaps that incur a larger price impact are arbitrages of liquidity pools with thin liquidity.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>source: <a href="https://dune.com/lido/wsteth-price-impact">lido dune</a></p></figcaption></figure>

## Yield Volatility

Lido protocol ETH LSD staking rewards consist of two parts (like for any other LSD protocol):

1. **Rewards from Consensus Layer** (Block Proposal Reward, Attestation Reward, Sync Committee reward) - consensus layer rewards decrease as more validators join and increase if more validators exit. The consensus layer rewards stay the same regardless of network traffic volume, so they are quite stable.
2. **Rewards from Execution Layer** (Txs priority tips and MEV tips) - execution layer rewards have high fluctuations because they are based on Ethereum network traffic volume. For example, when Ethereum network traffic increases, users pay higher priority tips and there is more opportunity for MEV executions.

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption><p>Source: <a href="https://dune.com/queries/1288160/2264095">dune</a></p></figcaption></figure>

The [ETH\_STORE](https://staking.ethermine.org/statistics) "Transparent Ethereum Staking Reward Reference Rate" shows the volatility of staking APR related to total staking rewards. Staking rewards vary on a daily basis for realized aggregated execution layer rewards, which is a much smaller variation compared to the aggregated APR rate. Deviations in the staking APR rate are also affected by changes in the amount of deposited or withdrawn ETH.\\

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption><p>source: <a href="https://staking.ethermine.org/statistics">https://staking.ethermine.org/statistics</a></p></figcaption></figure>

## Liquidity Analysis

wstETH is supported on all major DEXes on main net. The Lido dune dashboard shows (w)stETH/wETH liquidity - the most common trade route for those wanting to enter or exit a staked position. Most wstETH/ETH liquidity is on Curve, Maverick, Balancer and Uniswap. Curve has the largest wstETH/ETH liquidity pool and Uniswap has the most volume.

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption><p>source: <a href="https://dune.com/lido/wsteth-price-impact">lido dune</a></p></figcaption></figure>

Dex Guru shows that while most ETH paired liquidity is based on Curve, there is widespread usage on other exchanges too, particularly Balancer.\
\
The numbers referred to in the chart below is "exit liquidity". This means the total liquidity is not taken into account, only the tokens that make up the other side of the liquidity pool. This is especially important on stableswap exchanges because it is not uncommon for liquidity pools to be 90% + balanced towards one token.\
\
wstETH is a popular choice for projects to pair their tokens with due to its strong liquidity and its interest bearing nature which has a positive impact on liquidity, putting upwards pressure on the price of the paired token.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>source: <a href="https://dex.guru/liquidity/token/eth/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0">dex guru</a></p></figcaption></figure>

The largest wstETH liquidity pool is the AAVE/wstETH 80/20 pool on balancer with $110m deposited.

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption><p>source: <a href="https://dex.guru/liquidity/token/eth/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0">dex guru</a></p></figcaption></figure>

stETH has almost all of its liquidity on Curve and has seen a steady decline throughout 2023, in line with Lido's changes to liquidity subsidisation. Liquidity has been stable since mid 2023.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption><p>source: <a href="https://dex.guru/liquidity/token/eth/0xae7ab96520de3a18e5e111b5eaab095312d7fe84?amm=curve">dex guru</a></p></figcaption></figure>

The largest stETH liquidity pool is on Curve. The second largest is also on Curve. The smaller of the two is Curves "New Generation" (ng) pool that supports new upgrades such as dynamic fees or support for rebasing tokens, tokens with oracles, or ERC-4626.

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

According to Dex Guru, wstETH exit liquidity is $165,482,909 and stETH exit liquidity is $203,125,282 making approximately $368.5m total exit liquidity.

## Liquidity Utilization

Uniswap has the highest utilization rates of (w)stETH liquidity with nearly 100% volume to liquidity ratio.

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

## Leverage

Over 3.1m (w)stETH is used as collateral across DeFi counting for 31.77% of the total supply. Of the 3.1m, over 3m is used as collateral on Ethereum main net.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>source: <a href="https://dune.com/lido/wsteth-as-collateral">lido dune</a></p></figcaption></figure>

Aave v3 accounts for 36.8% of the total (w)stETH deposits, Spark has 25.5%, Maker 21.4% and Aave v2 10.5%. Aave, Spark and Maker account for almost 95% of all (w)stETH collateral deposits.

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption><p>source: <a href="https://dune.com/lido/wsteth-as-collateral">lido dune</a></p></figcaption></figure>

As ETH price has increased over the last few months there is minimal high risk collateral according to the Lido aggregated risk dashboard.

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/ddbb5d95-54ec-4aa0-8879-966d1f807032/latest">lido aggregated risk dashboard</a></p></figcaption></figure>

It is worth noting that most protocols do not offer any additional APY for deposits & that is true for AAVE, Spark and Maker so there is minimal liquidity rental from protocols.\
\
Lido also have a dashboard allowing the monitoring of key protocols debt positions [here](https://deepnote.com/@Lido-analytical-team/Collateral-risk-monitor-07af4ca5-ad04-49b8-b747-d05ec9f4ad31)

## Slippage

Onchain liquidity can absorb stETH swaps of around $100m with minimal slippage

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption><p>source: <a href="https://defillama.com/liquidity">defillama</a></p></figcaption></figure>

wstETH liquidity can absorb even larger sells, with a $250m sell resulting in 0.79% slippage. Around $300m sells will start to incur larger losses

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption><p>source: <a href="https://defillama.com/liquidity">defillama</a></p></figcaption></figure>

## Summary

As highlighted in the performance analysis summary, (w)stETH use as collateral seems to be the most obvious risk factor that could result in another depeg. Lido have measurments in place to try to mitigate this risk with their dedicated team for managing liquidity according to the usage of (w)stETH in DeFi & they have the ability to increase liquidity incentives if the risk is perceived to increase. DeFi protocols such as Aave have also capped deposits for wstETH, which should help to aleviate any short term fluctuations in demand for borrowing vs available on-chain liquidity.
