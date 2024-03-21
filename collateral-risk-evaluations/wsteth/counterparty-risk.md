# Counterparty Risk

This section addresses the persistence of stETH's properties from an ownership rights perspective (i.e. possession, use, transfer, exclusion, profiteering, control, legal claim). The reader should get a clear idea of (1) who can legitimately change properties of the collateral (e.g. minting additional units) and what their reputation is, (2) the extent that changes can be implemented and the effect on the collateral.

This section is divided into 4 subsections:

* Governance
* Decentralization of the LSD
* Economic Performance
* Legal

## Governance <a href="#id-51-governance" id="id-51-governance"></a>

### Governance Scope <a href="#id-511-governance-scope" id="id-511-governance-scope"></a>

**Aragon DAO**: [https://vote.lido.fi/](https://vote.lido.fi/)

Core system controls including contract upgrades and critical parameters are governed by LDO token holders. Votes are 72 hours with normal voting in the first 48 hours and only negative votes allowed in the final 24 hours. The quorum is 5% and votes require >50% approval to pass.

Contracts upgradable by DAO vote:

[LidoLocator](https://docs.lido.fi/contracts/lido-locator), [Lido](https://docs.lido.fi/contracts/lido), [StakingRouter](https://docs.lido.fi/contracts/staking-router), [NodeOperatorsRegistry](https://docs.lido.fi/contracts/node-operators-registry), [AccountingOracle](https://docs.lido.fi/contracts/accounting-oracle), [ValidatorsExitBusOracle](https://docs.lido.fi/contracts/validators-exit-bus-oracle), [WithdrawalVault](https://docs.lido.fi/contracts/withdrawal-vault), [WithdrawalQueueERC721](https://docs.lido.fi/contracts/withdrawal-queue-erc721), [LegacyOracle](https://docs.lido.fi/contracts/legacy-oracle)

Parameters and other functionality controllable by the DAO:

* Burn stETH to compensate for penalties/slashing losses
* Pause user submissions, withdrawals, oracle report submissions, and all token actions
* Set the fee and distribution of fees between the treasury and node operators
* Add or remove node operators and designate a staking limit

**Easy Track**: [https://easytrack.lido.fi/](https://easytrack.lido.fi/)

Easy Track is an optimistic sub-DAO with limited access controls. The Aragon DAO is the default admin, and an [emergency brakes multisig](https://etherscan.io/address/0x73b047fe6337183A454c5217241D780a932777bD) has the power to pause or cancel motions. Motions will pass unless a .5% of LDO vetoes the motion before it is enacted after a 72-hour timelock.

Three types of motions can be created via Easy Track and only by the authorized addresses:

* Node operator request to increase their own staking limit
* Allocate funds to the [LEGO program](https://lego.lido.fi/) (Lido Ecosystem Grants Organization)
* Allocate funds to the LOL (Liquidity Observation Lab) program

### Access Control <a href="#id-512-access-control" id="id-512-access-control"></a>

Several multisigs are used with limited priveleges, typically either as an emergency backstop or as committee with a treasury budget allocation.

**GateSeal committee multisig (3/6)**: [0x8772E3a2D86B9347A2688f9bc1808A6d8917760C](https://etherscan.io/address/0x8772E3a2D86B9347A2688f9bc1808A6d8917760C)

* Michael, [Curve.fi](http://curve.fi/)
* Ernesto, BGD Labs
* Andrew, Forta
* Sjorj, Lido on Ethereum Tooling team
* Skozin, Special Projects / Lido on Ethereum protocol team
* Kadmil, DAO Ops team

A GateSeal is a precautionary mechanic introduced to Lido V2 with [this proposal](https://research.lido.fi/t/lido-v2-gateseal-committee/4561). It is a contract that allows a designated address (ideally a multisig) to call pause on a set of predefined system contracts. It is a one-time use contract that is meant as a panic button since the DAO process requires a 72-hour timelock.

The [GateSeal Factory](https://etherscan.io/address/0x6c82877cac5a7a739f16ca0a89c0a328b8764a24) contract is used to deploy a GateSeal contract, which specifies the sealing committee address, the sealable contracts, the duration of the pause, and the expiration date of the GateSeal contract.

The [GateSeal](https://etherscan.io/address/0x1ad5cb2955940f998081c1ef5f5f00875431aa90) contract created here can pause the withdrawal queue (users’ side of withdrawals) and validator exit bus (Node Operators’ side of withdrawals). The pause duration is 6 days, and the contract expires in May 2024, regardless if it has been used. Another GateSeal can be created at that point, pending DAO approval.

**Emergency Brakes multisig (3/5)**: [0x73b047fe6337183A454c5217241D780a932777bD](https://etherscan.io/address/0x73b047fe6337183A454c5217241D780a932777bD)

* 0xCFfE0F3B089e46D8212408Ba061c425776E64322 - [@folkyatina](https://research.lido.fi/u/folkyatina)
* 0xdd19274b614b5ecAcf493Bc43C380ef6B8dfB56c - [@ujenjt](https://research.lido.fi/u/ujenjt) (Eugene Pshenichniy)
* 0x59f8d74fe49d5ebeac069e3baf07eb4b614bd5a7 [@theDZhon](https://research.lido.fi/u/thedzhon) (Lido on Ethereum protocol team)&#x20;
* 0x6f5c9B92DC47C89155930E708fBc305b55A5519A - [@kadmil](https://research.lido.fi/u/kadmil) (Victor Suzdalev)
* 0x2a61d3ba5030Ef471C74f612962c7367ECa3a62d - [@psirex](https://research.lido.fi/u/psirex) (Bogdan Kovtun)

The emergency brakes multisig has the PAUSE\_ROLE of the EasyTrack voting contract. When paused, the contract cannot create or enact motions. It is additionally an authorized bridging manager for L2 token bridging.

<figure><img src="https://hackmd.io/_uploads/ByxKGjVYh.png" alt=""><figcaption><p>Source: <a href="https://pod.xyz/podarchy/0x73b047fe6337183A454c5217241D780a932777bD?sidebar=0&#x26;selectedNode=%220xF0211b7660680B49De1A7E9f25C65660F0a13Fea%22">Pod.xyz</a></p></figcaption></figure>

**Deposit Security Committee Multisig (4/6)**: [0xC77F8768774E1c9244BEed705C4354f2113CFc09](https://etherscan.io/address/0xC77F8768774E1c9244BEed705C4354f2113CFc09)

The [DepositSecurityModule](https://etherscan.io/address/0xC77F8768774E1c9244BEed705C4354f2113CFc09) was created with a set of guardians callable in [getGuardians](https://etherscan.io/address/0xC77F8768774E1c9244BEed705C4354f2113CFc09#readContract#F9) as a mitigation to a [vulnerability](https://github.com/lidofinance/lido-improvement-proposals/blob/develop/LIPS/lip-5.md) of a possible malicious NO intercepting user deposits sent to the beacon chain.

The 4-of-6 multisig sign off on the calldata included in depositBufferedEth(), which can potentially steal user funds with malicious data. The contract allows any guardian to call pauseDeposits() in case suspicious activity is observed, potentially involving collusion between a malicious NO and a quorum of guardians.

**Lido dev team Multisig (3/5)**: [0x3cd9F71F80AB08ea5a7Dca348B5e94BC595f26A0](https://etherscan.io/address/0x3cd9F71F80AB08ea5a7Dca348B5e94BC595f26A0)

The Lido dev team multisig does not have substantial privileges within the system. It is authorized as a bridging manager for L2 token bridging

#### **Additional Committee Multisigs**

A number of [additional multisigs](https://docs.lido.fi/deployed-contracts/#lido-dao-multisigs) are given limited privileges to manage a portion of the treasury for certain operations. For example, the reWARDS multisig was recently approved with a spending budget of 2,100 ETH every 3 months ([tx](https://etherscan.io/tx/0xac7ccec0c11a204636ca2a660d73bfca772eaacd5d7076061b44d73324c509c8)).

Lido DAO ops multisigs Policy: [https://research.lido.fi/t/lido-dao-ops-multisigs-policy/4115](https://research.lido.fi/t/lido-dao-ops-multisigs-policy/4115)

### Distribution of Governance Tokens <a href="#id-513-distribution-of-governance-tokens" id="id-513-distribution-of-governance-tokens"></a>

The total LDO supply is 1 billion LDO tokens, of which 360m LDO tokens were allocated to the DAO treasury, 150m to founders (15%), 200m to initial developers (20%), 60.5m to validators and signature holders (6.5%) and 220m to investors (22.18).

<figure><img src="https://hackmd.io/_uploads/H149Gs4K3.png" alt=""><figcaption><p>Source: <a href="https://twitter.com/MessariCrypto/status/1517149027732647936">Messari</a></p></figcaption></figure>

At first glance, the initial LDO allocation looks highly centralized, as a separate allocation to founders and protocol developers isn't usual practice. In a relatively small investment round (Lido raised $2 million in a December 2020 round from a large group of investors), the protocol attracted key interest groups in the development of the protocol: professional staking service providers, founders of the largest Defi protocols, large VC funds, and other crypto entities like Argent.

After completing their seed round, Lido made two "treasury diversification deals" by selling LDO tokens from the treasury to VCs (3AC, Alameda, DragonFly, Coinbase) and other individual investors.

See a thorough analysis of the initial token distribution and the various players involved [here](https://mirror.xyz/tumilet.eth/Mtx7yu2RZLKmVhMWisZq\_GOtQoGSyTNFJ-J8fOoR6BE).

### Proposals Frequency <a href="#id-514-proposals-frequency" id="id-514-proposals-frequency"></a>

In January 2024, there were 2 Aragon DAO votes with a 50% pass rate. The pass vote #171 adressed a group of items in the same vote:

* Replacement of Jump Crypto with ChainLayer in the Lido on Ethereum Oracle set, as per a Snapshot vote.
* Deactivation of node operators Jump Crypto (id 1) and Anyblock Analytics (id 12) in the Curated Node Operators Registry, as discussed in the forum.
* Renaming of node operator HashQuark (id 20) to HashKey Cloud, following a forum request.
* Addition of stETH factories to facilitate funding for the Lido Contributors Group multisigs (RCC, PML, and ATC) in stETH via Easy Track, as suggested in the forum.
* An upgrade to the Easy Track setups to enable funding not only in DAI but also in USDT and USDC, following an audit by Oxorio. This upgrade includes granting EVMScripExecutor the permissions to transfer USDT and USDC with a single transfer limit of 2M, in addition to its current permissions.
* Conversion of the DAI top-up setup to include DAI, USDT, and USDC for all Lido Contributors Group multisigs (RCC, PML, and ATC), as well as for the LEGO multisig, as proposed in the forum.
* A recommendation to decrease the Easy Track limit for TRP multisig, in line with advice from the TRP committee.

The failed vote in January 2024 covered the same items but did not reach quorum.

In January 2024, there were 17 Easy Track motions with a 100% pass rate. 9 motions were node operator requests to increase their staking limit, 7 were requests from various committees to top up funding for their operations and the final vote was to add a participant to the reWARDS program.

### Participation <a href="#id-515-participation" id="id-515-participation"></a>

As there is a quorum of 5% voter participation, Aragon votes typically experience minimal voter turnout. In fact the majority of rejected votes are due to quorum not being met. Votes that pass usually have just over 5% of LDO voting, around 50m LDO.

Aragon's votes overwhelmingly appear to be procedural, and this is probably because the governance process involves forum discussion and Snapshot voting before moving to an on-chain vote.

An unusually contentious vote is [#29](https://vote.lido.fi/vote/29) to provide 30% of the 10% fee from staking rewards to LDO holders. The vote failed, not only due to a preference to grow the treasury but from a lack of clarity about the implementation of the proposal.

### Governance Attack Vectors <a href="#id-516-governance-attack-vectors" id="id-516-governance-attack-vectors"></a>

A proposal requires a minimum of 5% of the total voting power to be approved. Although the cost to successfully pass a malicious governance vote is likely much higher, we can calculate the minimum threshold required to pass a vote.

An attacker would need to acquire 50m LDO, currently valued at $3. The cost to acquire enough tokens at a minimum is $150m and is likely much higher due to slippage and the challenge of sourcing liquidity.

Alternatively, an attacker may attempt to borrow LDO, assuming a market exists with sufficient liquidity. LDO does not require locking to participate in governance, so it is conceivable an attacker could attempt to gain access to voting power temporarily.

The security of Lido governance depends on widely distributing the token such that it becomes inconceivable for a would-be governance attacker to gain access to enough voting power. LDO is remarkably well distributed, with nearly 37,000 token holders and just over 50% of tokens controlled by the top 10 addresses (including the Lido Treasury).

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Source: <a href="https://etherscan.io/token/tokenholderchart/0x5a98fcbea516cf06857215779fd812ca3bef1b32">Etherscan</a></p></figcaption></figure>

Note, however, that the GateSeal mechanism can pause system contracts immediately without undergoing the 72-hour vote period. The tradeoff here is required trust in the GateSeal committee to take action when necessary.

### Operational Safeguards <a href="#id-517-operational-safeguards" id="id-517-operational-safeguards"></a>

Lido has implemented numerous measures to safeguard its governance structure and address any possible security issues:

* **Aragon Vote Parameters**: The on-chain voting process via Aragon lasts 72 hours and is a two-phase system. The first phase lasts 48 hours, and the second lasts 24 hours. Votes require a 5% quorum and >50% approval to pass.
* **Two-phase Voting Mechanism**: This mechanism helps prevent last-minute governance attacks by dividing votes into two phases: the normal and the objection phases. During the objection phase, participants can only vote against the outcome if they hadn't previously voted or change their vote from 'for' to 'against'.
* **GateSeal**: GateSeal is a [contract](https://etherscan.io/address/0x6c82877cac5a7a739f16ca0a89c0a328b8764a24#code) that (pending DAO approval) grants a designated account the ability to pause a set of contracts for a limited duration. It acts as a panic button for essential contracts in emergencies, as it bypasses the usual 72-hour timelock. Lido has established an Emergency Brakes multisig with the capability to take such action with an expiry in May 2024.
* **Committees**: Various committees, such as LNOSG, LEGO, reWARDS, RCC, and the Referral Program Committee manage specific aspects of governance. Transactions from these committees usually go through the Easy Track, where voting is based on a vetoing principle.
* **Bridge Security**: Lido has conducted an audit of its deployed bridges with Oxorio and adopted Aave's governance cross-chain bridge contracts. While the Lido dev team multisig currently has the power to enable Layer-1 (L1) deposits in the bridge, the admin rights will transfer to the Lido DAO via the Aragon Agent App once the bridge is enabled. Consequently, any actions or changes to the bridges will necessitate explicit Lido DAO approval.

## Decentralization of the LST <a href="#id-52-decentralization-of-the-lsd" id="id-52-decentralization-of-the-lsd"></a>

### Number of Node Operators <a href="#id-521-number-of-node-operators" id="id-521-number-of-node-operators"></a>

There are 35 node operators for Ethereum in January 2024, up from 30 in May 2023.

### Validators per Node Operator <a href="#id-522-validators-per-node-operator" id="id-522-validators-per-node-operator"></a>

Of the 35 Ethereum NO's, the validators per NO range from 500 to 10001. The average per NO is 8207.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

### Market Share per Validator <a href="#id-523-market-share-per-validator" id="id-523-market-share-per-validator"></a>

Lido typically avoids over-concentration by limiting the global ETH stake held by any single operator. The staking pool distributes the deposits uniformly (round-robin) to node operators based on the remaining capacity in each validator's slot. For staking amounts exceeding 32 ETH, the stake is distributed among several validators.

Despite well-balanced stake distribution, some operators exceed the 1% soft-target articulated in the [Lido Scorecard](https://lido.fi/scorecard), signaling the need for additional Node Operators. The image above shows an orange line that represents the 1% marketshare target.

The Gini coefficient of stake distribution (shown below) increases when there are new NO onboardings, but over time the trend is toward a more balanced stake distribution.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

### Validator Enter/Exit (Churn) <a href="#id-524-validator-enterexit-churn" id="id-524-validator-enterexit-churn"></a>

ETH staking withdrawals went live with the Shanghai/Capella upgrade as of April 12, 2023, allowing validators to exit. 29,161 validators have exited amounting to 1,404,764.5 ETH withdrawn. On all timeframes the value withdrawn is significantly lower than depoits.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Past 7 days: 14th - 21st Feb 2024</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Past 30 days: 21st Jan -21st Feb 2024</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>All time. Source: <a href="https://www.rated.network/o/Lido?network=mainnet&#x26;timeWindow=all&#x26;viewBy=aggregate">Rated.network</a></p></figcaption></figure>

### Stakers per Validator <a href="#id-525-stakers-per-validator" id="id-525-stakers-per-validator"></a>

There are 368,629 stETH and 8,863 wstETH holders with a total supply of 9,804,591 stETH. The average stETH per address is 25.98. At 32 ETH per validator, there is an average of 1.23 stakers per validator.&#x20;

The average ETH staked is 26 ETH per address due to a small number of large stakers, the most common deposit value is \~$1000, and the distribution is heavily skewed toward low-value deposits.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Source: <a href="https://dune.com/queries/96708/193815">Dune Analytics</a></p></figcaption></figure>

### Stake Distribution Across Geographic Jurisdictions <a href="#id-526-stake-distribution-across-geographic-jurisdictions" id="id-526-stake-distribution-across-geographic-jurisdictions"></a>

NO stake is most heavily concentrated in Europe with nearly 60% of overall stake. There is minor representation in Asia/Pacific countries (\~10%) and no representation in South America or Africa.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

The following image shows the number of NO's across each jurisdiction, which corresponds with the amount of ETH staked by region.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

### Node Software Diversity <a href="#id-527-node-software-diversity" id="id-527-node-software-diversity"></a>

Vouch is a specialized validator client that is beacon node agnostic, allowing it to work with multiple beacon nodes. Overall, client diversity in Lido is consistent with that of the overall Ethereum network with less presence of Prysm and more of Teku.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

Due to the inaccuracy of fingerprinting and the prevalent use of Vouch in Lido (allowing multiple Beacon Nodes of varying client types to be tied to a single validator), there are inconsistencies between the data shown above and client diversity metrics on third-party platforms.



Execution Layer Client diversity is heavily reliant on Geth although steady progress made since Merge (Q2/22) in improving minority client usage, and especially evident in Q4 as a result of both the Wave 5 onboarding round as well as existing NOs making infra changes.  There are initiatives to reduce the reliance on geth further according to the [Lido forum](https://research.lido.fi/t/ethereum-node-operator-el-diversity-improvement-commitments/6459/4)

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption><p>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

### Node Hosting Infrastructure <a href="#id-528-node-hosting-infrastructure" id="id-528-node-hosting-infrastructure"></a>

Just under half of node hosting infra is by public cloud almost a third by dedicated server infra. AWS makes up the largest portion of public cloud hosting followed by GCP and Digital Ocean. Between them they make up around 1/3 of all node hosting infra.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p><br>Source: <a href="https://app.hex.tech/8dedcd99-17f4-49d8-944e-4857a355b90a/app/3f7d6967-3ef6-4e69-8f7b-d02d903f045b/latest">VaNOM Report</a></p></figcaption></figure>

## Economic Performance <a href="#id-53-economic-performance" id="id-53-economic-performance"></a>

### Revenue Source <a href="#id-531-revenue-source" id="id-531-revenue-source"></a>

5% of stETH staking yield is directed to the [Lido Treasury](https://etherscan.io/address/0x3e40D73EB977Dc6a537aF587D48316feE66E9C8c).

Revenue depends on the ETH consensus layer rewards, the execution layer rewards (MEV and network usage), the amount of ETH staked on Lido, and the USD price of ETH.

### Revenue <a href="#id-532-revenue" id="id-532-revenue"></a>

As of June 21, 2023, there is 9.73m ETH staked on Lido, earning 3.83% APY. The effective revenue captured by the protocol is 0.19% APY on the stETH supply.

[DeFiLlama](https://defillama.com/protocol/lido?tvl=false\&revenue=true\&events=false\&medianApy=true\&denomination=ETH\&groupBy=daily) estimates the annual revenue as $88.9m by taking the last 30 days of revenue and multiplying it by 12. Thismore than twice their revenue for the same time last year.

This estimated revenue may be highly variable depending on ETH price volatility, ETH staking yield, and the amount of ETH staked on Lido.

### Net Profit <a href="#id-533-net-profit" id="id-533-net-profit"></a>

Steakhouse Financial and Lido DAO have created a [Dune dash](https://dune.com/steakhouse/lido-safu) that tracks Lido's financial activities on Ethereum. They show monthly P\&L broken down into the following categories:

* Net revenue = Gross rewards - Rewards to stakers
* Cost of Revenue = Net revenue - Node operator fees - slashing provision - other
* Operating expenses = all DAO funding transfers to grantee service companies, committees, and third-parties
* Liquidity expenses = all DAO funding transfers specifically for funding liquidity incentive programs such as Curve rewards distributors

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>Source: <a href="https://dune.com/queries/2464243/4058500">Dune Analytics</a></p></figcaption></figure>

Figures are month-to-date and may be subject to change. June 2023 was Lido's first month in the black and they have hovered just above or just below break even since. The primary reason for no longer running at a huge loss has been the reduction in liquidity expenses.

## Legal <a href="#id-54-legal" id="id-54-legal"></a>

_See also the llama risk team's general_ [_LSD Legal Framework Considerations_](https://docs.google.com/document/d/e/2PACX-1vRQttlfMTK-kUzPAn\_Rx0Mwt\_K7pVYK-w27AbxU7iFxMqZctme2Sd\_PAhpBHCmVMAUsA7B1KNhVTojH/pub)

### Legal Structure <a href="#id-541-legal-structure" id="id-541-legal-structure"></a>

In the docs section of the website, Lido outlines how the user interface hosted on [lido.fi](https://lido.fi/) is managed. Lido DAO is depicted as a Decentralised Autonomous Organisation that governs the liquid staking protocols by deciding on key parameters. Among the core functions of Lido DAO are building, deploying, updating, and deciding on key parameters of liquid staking protocols, approving incentives for parties that contribute to DAO’s goals, and managing Node operators.

On March 22nd, 2023, [a proposal](https://research.lido.fi/t/legal-engineering-rfc-rfp-establish-lido-legal-entities/1790) was made to establish Lido legal entities. This proposal indicates that DAO needs to acquire expert advice, conduct research, and engineer the creation of a legal wrapper. A relevant finding includes the compensation for legal entity incorporation expenses, [as published](https://lego.lido.fi/compensation-of-lido-legal-entity-incorporation-expenses-to-eric-hill) by the Lido Ecosystem Grants Organization.

While the exact details of the legal structure are not publicly disclosed, it's safe to assume that Lido has chosen the Cayman Islands as the location to establish its entity. This assumption is supported by references in the [Terms of Use](https://lido.fi/terms-of-use) - “that the Interface shall be deemed to be based solely in the Cayman Islands and that although the Interface may be available in other jurisdictions, its availability does not give rise to general or specific personal jurisdiction in any forum outside the Cayman Islands.” Furthermore, the choice of law clause stipulates that the laws of the Cayman Islands govern relations with users.

### Licenses <a href="#id-542-licenses" id="id-542-licenses"></a>

The Cayman Virtual Asset Service Providers Act (VASP Act), revised in 2020, established a comprehensive regulatory registration and licensing system for VASPs. This Act enforces FATF Recommendation 15 (New technologies), focusing on international standards to counter money laundering, financing of terrorism, and proliferation. Every blockchain-based token that can be technically transferred or exchanged falls under the definition of a virtual asset according to the VASP Act, regardless of its programmed properties or its intended use. The act doesn't differentiate between what are typically referred to as utility tokens, security tokens, and stablecoins. However, "virtual service tokens" are not considered virtual assets. The VASP Act excludes "virtual service tokens," which are "a digital representation of value which is not transferable or exchangeable with a third party at any time and includes digital tokens whose sole function is to provide access to an application or service or to provide a service or function directly to its owner."

We cannot confirm Lido's entry on the [public register of regulated entities](https://www.cima.ky/search-entities-cima/get\_search\_data) maintained by the Cayman Islands Monetary Authority.

A common form for a DAO legal wrapper is a foundation - a unique corporate structure in the Cayman Islands with independent legal status and limited liability. **The Cayman Islands Foundation Companies Act 2017** (in force since 2017) allows a foundation to become devoid of members (i.e., shareholders), thereby becoming an entity without an owner. The General Registry of the Cayman Islands offers a general search for Companies, Partnerships, and Trusts. We estimated numerous possible matches but could not confirm the details of the assumed DAO structure as the [comprehensive excerpt is fee-gated](https://online.ciregistry.gov.ky/).

The above findings do not intend to discredit Lido and their corporate setup nor instill a preference towards a particular legal structure or jurisdiction. We are not lawyers or legal advisors, so the conclusions herein cannot be considered a binding legal analysis. Our attempts are devoted to finding out the type of establishment (if any) and assessing the risk level of the chosen setup for end users. Consistent with the reviewed outputs, we can safely agree that Lido has taken all possible actions to mitigate the legal risk arising from the activities of a decentralized organization in an unregulated environment (i.e., staking services).

### Enforcement Actions <a href="#id-543-enforcement-actions" id="id-543-enforcement-actions"></a>

No reported actions by SEC directed toward Lido.

### Sanctions <a href="#id-544-sanctions" id="id-544-sanctions"></a>

Lido does not onboard U.S. persons residing, incorporated, or conducting business in the United States, as well as persons from any country under economic sanctions or embargoes, such as Belarus, Burundi, Crimea, and Sevastopol, Cuba, Democratic Republic of Congo, Iran, Iraq, Libya, North Korea, Somalia, Sudan, Syria, Venezuela, and Zimbabwe - see [Section 7 of Lido's Terms of Use](https://lido.fi/terms-of-use).

The restrictions also apply to users who are directly or indirectly involved with any blockchain address listed on any sanctions list maintained by the United States, the United Kingdom, the European Union or any of its member states, or the United Nations or any of its member states.

While Lido has not revealed what type of blockchain analytics software it uses, the prohibitions outlined in the terms of use explicitly state the platform's stance towards attempts at circumvention.

Non-compliance with Section 7 results in access restriction, as indicated in the disclaimer at the top of the Terms of Service:

> "If you do not meet the eligibility requirements set forth in Section 7 of the Terms or are otherwise not in strict compliance with these Terms, you are expressly prohibited from using, accessing, or deriving any benefit from the Interface. You must not attempt to access or use the Interface if you don't meet these requirements. The use of a virtual private network (e.g., a VPN) or other means by ineligible persons to access or use the Interface is prohibited. Engaging in such prohibited uses may attract legal liability for fraudulent use of the Interface".

### Liability Risk <a href="#id-545-liability-risk" id="id-545-liability-risk"></a>

The disclaimer on regulatory uncertainty in Section 11 states that the platform or any tokens or blockchains could potentially be negatively affected by various legal or regulatory interventions, such as inquiries, actions, lawsuits, investigations, claims, penalties, or judgments. Such occurrences may pose serious hurdles or limitations to the User's ability to continue using and benefiting from these assets and technologies.

The Limitations of Liability outlined in Section 15 apply to the fullest extent permitted by applicable law. The platform shall be indemnified against a user’s violation of the Terms of Use or any rights of other persons.

The arbitration agreement is incorporated into Section 1. All unresolved disputes or claims shall be finally and exclusively settled by arbitration administered by the London Court of International Arbitration under the LCIA Arbitration Rules.

## Adverse Media Check <a href="#id-546-adverse-media-check" id="id-546-adverse-media-check"></a>

It's worth noting that Lido's native governance token, LDO, experienced nearly a 10% dip on rumors of receiving a Wells notice from the SEC. Price movement has no obvious correlation with official or unofficial publication on this topic.

Open search for negative news pointing to Lido shows several attempts of unidentified perpetrators to impersonate Lido Finance for pre-sale or airdrop of tokens. Users were [asked](https://www.reddit.com/r/LidoFinance/comments/w0ji2r/lplidocom\_scam/) to connect their MetaMask wallet to exchange these tokens for LDO, which is a typical tactic used in phishing scams where malicious actors trick victims into revealing their private keys or seed phrases. Lido Finance issued a [public warning](https://twitter.com/LidoFinance/status/1323020795342446592?lang=bg) for potential scams that imitate the Platform, rather than actions taken by the DAO itself. Based on the information available as of June 2023, there are no public records or reports that suggest Lido Finance has been involved in any unlawful activities.
