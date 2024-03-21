---
description: >-
  This section will summarize the findings of the report by highlighting the
  most significant risk factors in each of the three risk categories: Market
  Risk, Technology Risk, and Counterparty Risk.
---

# Risk Management

## Market Risk <a href="#id-611-market-risk" id="id-611-market-risk"></a>

### **LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?**

Lido is a clear market leader, commanding over 70% of the LSD market since its inception in December 2021. It has been integrated widely as collateral into several DeFi lending protocols such as MakerDAO and Aave, and has over $350m worth of exit liquidity on DEXs such as Curve, Balancer and Uniswap. The [DeFillama Liquidity Tool](https://defillama.com/liquidity) estimates a swap size of $115m (40k stETH) would be required to produce >1% slippage. stETH/wstETH account for 2/3 of all LSD trading volume, and while its market share does appear to be decreasing with all the new competition, the amount of staked Ether is still increasing.\
\
30% of all (w)stETH is used as collateral on various lending platforms. While available liquidity should be sufficient to absorb liquidations in most cases, extreme market conditions may cause a liquidation cascade that drains all available exit liquidity. The LOL comitee is tasked with mitigating this risk however Bao should take measures to monitor this themselves too. A weekly analysis of risky positions and available liquidity as well as ad-hoc evaluations on market volatility.

### **VOLATILITY: Has the LSD had any significant depeg event (post merge)?**

Arriving at the merge in September 2022, stETH had been experiencing a prolonged depeg event since the Terra collapse in May 2022. It recovered around the time of the merge, but experienced a second, relatively minor depeg in November 2022. A whale [removed 88,131](https://twitter.com/lookonchain/status/1595719510387875840?s=20) ETH from the stETH/ETH pool, causing a sharp depeg to .9682 that did not completely recover until January 2023.

Since ETH withdrawals have been activated in April 2023, the liquid staking basis has markedly stabilized, meaning stETH has maintained a consistent peg against ETH. We do observe, however, that staking yields have been declining as demand for staking continues to boom. Reduced yields may affect demand for LSDs such as stETH, resulting in the need to process large amounts of withdrawals.

Withdrawals are not instantaneous and can take weeks to process if the exit queue is long or a major slashing event occurs. Tumultuous market circumstances or network problems within Lido or Ethereum at large may precipitate a depeg in the future that cannot be immediately arbitraged.

## Technology Risk <a href="#id-612-technology-risk" id="id-612-technology-risk"></a>

### **SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?**

Lido V2 codebase has undergone extensive audits in 2023 by various auditing firms including Oxorio, Statemind, Hexens, MixBytes, and Certora. There is also an active bug bounty program with ImmuneFi since May 2021. Lido discloses network problems that result in losses in their Post Mortem blog. Losses have historically been minimal, and where applicable, Lido has reimbursed affected users.

The recent upgrade to Lido V2 in May 2023 allows additional functionality, including ETH withdrawals. This increases the uncertainty of smart contract security due to the short duration on mainnet.

### **DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?**

In case of no finality on the Consensus Layer, Lido's oracle daemons may stop pushing regular updates (set to 225 epochs or 1 day), preventing rebases from taking place. If sanity checks fail (on max APR or total staked amount drop), this could cause significant disruptions in Lido’s operations, including incorrect distribution of rewards and liquidity mismanagement.

Due to extreme market events on November 9 and 11, 2022, a protocol-enforced sanity check was erroneously triggered that prevented Oracle updates and caused a disruption in rewards distribution. The event was documented in this [post mortem](https://blog.lido.fi/postmortem-disrupted-rewards-distribution-due-to-missed-oracle-reports/).

Lido has a reliable Chainlink pricefeed oracle available for both stETH/ETH and stETH/USD pairs.

Ongoing monitoring of the reliance on Geth is recommended quarterly.

## Counterparty Risk <a href="#id-613-counterparty-risk" id="id-613-counterparty-risk"></a>

### **CENTRALIZATION: Are there any significant centralization vectors that could rug users?**

Concerning smart contract access control, Lido has taken precautions to protect contract upgrades and other critical system controls behind an Aragon DAO governed by LDO tokenholders. For convenience, EasyTrack optimistic voting is used for a limited subset of recurring vote types. LDO has never experienced a governance attack, and while it may be theoretically exposed to such a risk by not requiring a lock to participate in governance, LDO does not realistically have market liquidity or presence on lending platforms to be a concern at this time.

A number of multisigs have privileges limited to specific functions, such as the GateSeal committee's ability to emergency pause the system. The GateSeal further decreases the likelihood of a governance attack, although with the tradeoff of requiring trust in the committee to take necessary action.

Lido also takes measures to decentralize its permissioned set of node operators by monitoring the distribution of stake across NOs, and diversity metrics such as clients, staking infrastructure, and geographies of operation. These precautions minimize the risk of a major slashing event.

In short, users are required to trust in the reliable performance of third-party NOs, but Lido has taken precautions to avoid centralization of the NO network.

### **LEGAL: Does the legal analysis of the protocol suggest any cause for concern?**

While the regulatory climate surrounding DAO and DeFi remains uncertain, it is unclear how an enforcement action might be carried out against a DAO. As Lido is governed by LDO tokenholders, legal action is unlikely to disrupt the platform's operations. A potential centralization risk is from the large proportion of NOs operating in Europe (60% of ETH staked in Lido), which increases the network's risk exposure to regulatory action in those jurisdictions.

There is no discernible evidence that Lido has been involved with any unlawful activities and it has not received any enforcement actions. The interface [Terms of Use](https://lido.fi/terms-of-use) takes reasonable precautions to limit Lido's liability. While enforcement actions are always a possibility in an uncertain regulatory climate, Lido appears to be reasonably protected.

## &#x20;<a href="#id-614-risk-rating" id="id-614-risk-rating"></a>
