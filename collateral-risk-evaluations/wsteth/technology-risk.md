# Technology Risk

This segment looks at the technological stability of the collateral, focusing on two main concerns: the emergence of technological risks that could alter the collateral's inherent characteristics (eg, unaddressed vulnerabilities highlighted in audits), and the potential complications arising from composability or dependencies (such as the availability of a dependable price feed oracle)

## Smart Contract Risk

The Lido V2 protocol update brought significant enhancements, including the option for stETH token holders to redeem their tokens for native Ether following the Ethereum Shanghai/Capella hard fork. It also introduced staking modules to the StakingRouter contract and improved Oracle contract consensus mechanisms, enabling the handling of large data volumes without limits.

In 2023, the Lido V2 codebase was rigorously audited by several firms:

* **Oxorio**: [on-chain](https://github.com/lidofinance/audits/blob/main/Oxorio%20Lido%20V2%20On-chain%20Audit%20Report%2006-23.pdf) and [off-chain](https://github.com/lidofinance/audits/blob/main/Oxorio%20Lido%20V2%20Off-chain%20Audit%20Report%2006-23.pdf) audits (May)
* **Statemind**: [Deployment Validation](https://github.com/lidofinance/audits/blob/main/Statemind%20Lido%20V2%20Deployment%20Validation%2005-2023.pdf), [Upgrade Template](https://github.com/lidofinance/audits/blob/main/Statemind%20Lido%20V2%20Upgrade%20Template%20Audit%20Report%2005-2023.pdf), [V2](https://github.com/lidofinance/audits/blob/main/Statemind%20Lido%20V2%20Audit%20Report%2004-23.pdf) and [GateSeals ](https://github.com/lidofinance/audits/blob/main/Statemind%20GateSeals%20Audit%20Report%2004-2023.pdf)audits (April-May),&#x20;
* **Hexens**: [Oracle](https://github.com/lidofinance/audits/blob/main/Hexens%20Lido%20V2%20Oracle%20Security%20Review%20Report%2005-23.pdf), [V2](https://github.com/lidofinance/audits/blob/main/Hexens%20Lido%20V2%20Smart%20Contract%20Audit%20Report%2004-23.pdf) audits (April-May)
* **MixBytes**: [V2 audit](https://github.com/lidofinance/audits/blob/main/MixBytes%20Camp%20Lido%20V2%20Contest%20Report%2004-23.pdf) (April)
* **Certora**: [V2 audit](https://github.com/lidofinance/audits/blob/main/Certora%20Lido%20V2%20Audit%20Report%2004-23.pdf) (April)

### Audit Insights

Although all identified issues were recognized, they were not rectified due to reasons such as their low likelihood of occurrence, existing mitigations, concerns over worsening the user experience, and the risk of new vulnerabilities. The deployment and initial setup of the version 2 release also underwent audit scrutiny. Notably, due to the immense value they secure, Lido's contracts are among the most thoroughly audited in the smart contract space.

### Bug Bounty Program

Since May 2021, Lido has operated a bug bounty program through [ImmuneFi](https://immunefi.com/bounty/lido/), offering rewards up to $2 million. While not all payouts are disclosed, Lido has [awarded $250,000](https://lido.fi/bug-bounty) across seven bug bounties to date. One notable instance disclosed in a [post mortem](https://blog.lido.fi/vulnerability-response-update/), involved a vulnerability disclosed via the program in 2021 that could have allowed an unauthorized party to misappropriate user funds.

### Contract Upgradability

Lido utilizes upgradeable proxy contracts for state storage, each directing to an implementation contract that manages the proxy's state. Through DAO votes, these implementation contracts can be updated, though the implementations themselves remain immutable, only altering the state of the calling (proxy) contract.

A comprehensive list of deployed contracts is available at: [https://docs.lido.fi/deployed-contracts/](https://docs.lido.fi/deployed-contracts/).

### Developer Activity

13 GitHub users with more than 10 commits have contributed to the [lidofinance/lido-dao repository](https://github.com/lidofinance/lido-dao) over the last 12 months.

### SC Maturity <a href="#id-416-sc-maturity" id="id-416-sc-maturity"></a>

The first contracts were deployed in November 2020. Since then, Lido has deployed several upgrades, the latest one being the [Lido V2 upgrade](https://blog.lido.fi/lido-v2-launch/) as of May 2023. This introduced two new features: ETH staking withdrawals and a Staking Router that allows modularity for new NO onboarding strategies. The recent upgrade increases uncertainty about smart contract security, although the contracts have been heavily audited.

### Previous Incidents <a href="#id-417-previous-incidents" id="id-417-previous-incidents"></a>

Lido discloses incidents affecting the network in the [Post Mortem](https://blog.lido.fi/category/postmortem/) section of the Lido Blog.

Most recently, a [post mortem](https://blog.lido.fi/post-mortem-launchnodes-slashing-incident/) was issued detailing a slashing event that effected 20 nodes run by Launchnodes and resulted in a 28.6 ETH loss. Launchnodes compensated stakers for the full amount meaning that there was no effect to the rewards of stETH holders. 28.6 ETH would have been a tiny portion of the daily rewards and a negligible loss for stETH holders.

## Product and Layer Composability <a href="#id-42-product-and-layer-composability" id="id-42-product-and-layer-composability"></a>

### Dependencies <a href="#id-421-dependencies" id="id-421-dependencies"></a>

There is no native communication between Ethereum’s Consensus layer and Execution layer, so Lido’s system architecture requires independent entities that run daemons to sync the system periodically.

An initial oracle set consisting of 5 Lido-approved Node Operators (NO) with a required quorum of 3/5 was expanded by [governance](https://snapshot.org/#/lido-snapshot.eth/proposal/0xcbf534335fe07c046caa933e1623ac38bfb3d1890ab825264a0b47415cf7799b) decision in [January 2023](https://vote.lido.fi/vote/149) with 4 additional oracle operators and a quorum of 5/9.

The on-chain portion of Lido's Oracle mechanism consists of the [AccountingOracle](https://docs.lido.fi/contracts/accounting-oracle) and the [ValidatorExitBusOracle](https://docs.lido.fi/contracts/validators-exit-bus-oracle):

**AccountingOracle**: Oracles assigned by the DAO report daily on changes to DAO-controlled address balances that fluctuate due to reward accumulation and slashing penalties.

**ValidatorExitBusOracle**: Delivers validator exit requests to Lido NO’s.

Together these processes are responsible for rebasing user balances, distributing stake, processing validator exit requests, and putting the protocol into bunker mode. [Bunker mode](https://research.lido.fi/t/withdrawals-for-lido-on-ethereum-bunker-mode-design-and-implementation/3890) may be initiated during severe events (e.g. mass slashing), which temporarily pauses withdrawal requests until the event has been resolved to prevent sophisticated users from frontrunning negative consequences.

### **Security precautions**

Lido’s Oracle system is equipped with multiple layers of security measures. These have been designed to guard against known attack vectors, ensuring the integrity and robustness of the system.

**Decentralization and Consensus Mechanism**: Lido employs multiple independent Oracle nodes for data collection and report generation. These nodes operate independently, reducing the risk of a system-wide failure if one node is compromised. Lido requires a 5/9 quorum of identical reports to accept Oracle updates.

**EIP-2335 Encryption Standard**: Lido employs the EIP-2335 standard for encryption, specifically in the Ejector module. The exit messages containing sensitive information are encrypted following this standard, and the Ejector module decrypts these files using a password stored in the MESSAGESPASSWORD environment variable.

**Sanity Checks**: Lido’s Accounting module conducts sanity checks on Oracle reports. By limiting changes to a 10% APR increase and a 5% decrease in stakes, these checks guard against sudden, extreme alterations that could indicate Oracle misbehavior or system manipulation.

**Governance Control**: The sanity check values can be adjusted by governance in exceptional circumstances.

### Withdrawal Processing <a href="#id-422-withdrawal-processing" id="id-422-withdrawal-processing"></a>

[Withdrawal requests](https://blog.lido.fi/just-how-fast-are-ethereum-withdrawals-using-the-lido-protocol/) are not processed immediately. If there is enough ETH in the protocol buffer, the request can be processed in under a day.

For amounts above 1000 ETH, the protocol divides the request into multiple 1000 ETH requests. Lido estimates withdrawals in the 1000-5000 ETH range can take 2 days to process, unless a shortage in the buffer causes a delay (up to 5-9 days). Requests in the 5k - 100k range are expected to take 4-10 days, and >100k to take 2 weeks to process.

In all cases, withdrawal times may be higher if the exit queue is long or a major slashing event triggers "bunker mode". During bunker mode, withdrawal requests halt until the situation has resolved, between 1 and 36 days.

The size of the protocol buffer shown below combines the quantity of ETH in the protocol not allocated to NOs, combining ETH in stETH, the withdrawals vault, and the withdrawals queue:

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Source: <a href="https://dune.com/queries/2478093/4076619">Dune Analytics</a></p></figcaption></figure>

Lido offers a suggestion table for determining the optimal exit path from stETH. Factors include the user's desired withdrawal size, the amount of ETH in the protocol buffer, the size of the withdrawal queue, and the possibility of bunker mode.

![Source: Lido Blog](https://hackmd.io/\_uploads/ryv8Mi4t3.png)

Lido also offers a [Dune Dash](https://dune.com/lido/lido-v2) that shows current and historical data about withdrawal demand and processing time.

## Oracle Pricefeed Availability <a href="#id-43-oracle-pricefeed-availability" id="id-43-oracle-pricefeed-availability"></a>

### Understanding the Oracle <a href="#id-431-understanding-the-oracle" id="id-431-understanding-the-oracle"></a>

The pricing data for the stETH/ETH and stETH/USD have a Chainlink price feed available, a widely-adopted aggregated solution. This oracle system collects data from multiple (16 and 19, respectively) oracle providers, drawing information from on-chain and centralized exchange (CEX) sources. A consensus of sources is required to establish a price, ensuring a robust and reliable price feed resistant to potential manipulation.

One crucial detail is the method to determine the conversion rate between stETH and wstETH. [stEthPerToken](https://etherscan.io/address/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0#readContract#F10) of the wstETH contract presents the conversion value of stETH to wstETH. This rate is fundamental to calculating collateralized debt positions (CDPs) and determining their wstETH/USD conversion.

Other Oracle price feeds, such as API3, also offer a stETH/ETH price feed. While these alternatives exist, they are less commonly used by CDPs that offer wstETH/stETH as collateral.

Furthermore, in the DeFi lending market, some protocols have adopted a 1:1 ratio for the stETH/ETH pair. This fixed peg system simplifies the price relationship and is gas-efficient but also introduces significant risks. Market volatility and delayed arbitrage from the withdrawal mechanic can cause a prolonged depegging event. In such a situation, it could lead to the creation of bad debt for the lending protocol.

## Token Liquidity and Distribution <a href="#id-432-token-liquidity-and-distribution" id="id-432-token-liquidity-and-distribution"></a>

Liquidity for the stETH token is concentrated on Curve. Curve also accounts for around 95% of the stETH volume. wstETH liquidity is more evenly spread over multiple exchanges with Balancer having the largest share. Uniswap also accounts for a large portion of  wstETH/ETH liquidity and captures around 95% of the wstETH volume.&#x20;

Notably, any of the liquidity pools for both stETH and wstETH are concentrated liquidity. As shown above in the analysis of slippage it would take hundreds of millions to move the price more than 1% & maintaining any discount on the underlying asset price is likely to be met by arbitrageurs willing to wait for withdrawals.&#x20;

## Attack Vectors <a href="#id-433-attack-vectors" id="id-433-attack-vectors"></a>

**High Dependency on a Single Protocol:** The stETH/ETH pair relies heavily on Curve for its liquidity pool. With such a high concentration of liquidity in a single protocol, the system becomes more susceptible to attacks aimed at manipulating this pool. An attacker could cause substantial disruptions to the stETH/ETH market by introducing volume variations to influence the price should they accumulate a significant share of the pool.

**Data Refresh Frequency:** The CHainlink oracle pushes price updates on a 1-hour heartbeat or a price deviation of more than 1%. This poses a risk of the update not being triggered promptly.

### Associated Vulnerabilities <a href="#id-434-associated-vulnerabilities" id="id-434-associated-vulnerabilities"></a>

**Bad Debt Creation:** In a successful price feed manipulation attack, one direct impact could be the creation of bad debt for the Protocol. Lending protocols rely on accurate price feeds to maintain appropriate collateralization ratios. If the price feed is manipulated to reflect an inaccurate price, attackers may perform malicious actions to create bad debt.

**Faulty Liquidation:** If an oracle is manipulated to drastically lower the price of a collateral asset in a lending protocol, it could trigger unjust liquidations of user positions, causing financial losses and disrupting the normal operations of the protocol.



