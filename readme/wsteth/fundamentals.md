---
description: >-
  This section will look at the tokenomics, node operators, governance and
  system architecture to identify potential risks.
---

# Fundamentals

## **Tokenomics**

* **Supply Mechanics:** wstETH is a permissionless ERC20 wrapper representing a user’s proportionate share of the total supply of stETH tokens. stETH is redeemable for a corresponding balance of ETH held by the Lido staking contract. When ETH is contributed to the protocol, it is distributed among various node operators. These operators then send the ETH to their assigned validators. stETH employs a rebasing mechanism, where the amount of stETH in holders' wallets increases automatically to reflect earned staking rewards, representing the growing value of their staked ETH.
* **Inflation/Deflation Factors:** Influenced by Ethereum staking rewards.
* **Distribution Model:** Equitable distribution among stakers.
* **Business Model:** A portion of staking rewards are split between the treasury and node operators with the remainder distributed to stETH holders via rebase. The current fee split can be checked with the [`getFeeDistribution`](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84#readProxyContract#F21) function. Currently 10% of staking rewards are taken as fees and split evenly between node operators and the treasury.

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption><p>Source: <a href="https://tokenterminal.com/terminal/projects/lido-finance">TokenTerminal</a></p></figcaption></figure>

## Nodes

Lido works with a select group of professional node operators chosen through its DAO governance. While the selection process is transparent, the number of node operators is relatively limited and can be viewed with the [`NodeOperatorsRegistry`](https://etherscan.io/address/0x55032650b14df07b85bF18A3a3eC8E0Af2e028d5) function. [Rated.network](https://www.rated.network/o/Lido?network=mainnet\&timeWindow=all\&viewBy=operator\&page=1) also provides an overview of their performance.

Slashings will impact the yield generated and passed to stETH holders. We can see from rated that to date there have been 411 slashing events with a total of 0.016% of rewards lost.

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption><p>source: <a href="https://www.rated.network/o/Lido?network=mainnet&#x26;timeWindow=all&#x26;idType=pool&#x26;viewBy=operator&#x26;page=1">rated.network</a></p></figcaption></figure>

### **Node Operator Onboarding**

Node Operators can apply to become part of the Lido network and are approved in waves by LDO holders. While there is no set criterea for onboarding Lido they do look for Node operators to have a good performance history, be able to show that they are robust which may include diverisified software and hardware infrastructures, disaster plans, and risk management protocols etc. In addition their ethos should be aligned with the underlying network they secure.

Lido V2 introduces the Staking Router, a transformative upgrade from its previous single operator registry. This new feature brings increased versatility and diversity to validator operations in several ways:

1. **Distributed Validator Technology (DVT):** Enhances decentralization by distributing validators across multiple clients and geographies.
2. **Community Module:** Allows permissionless participation of node operators with dynamic collateral requirements based on the operator’s reputation.
3. **Off-Chain or Layer 2 Module:** Aims to reduce gas costs by keeping validator keys off-chain or on Layer 2 solutions.
4. **Solo Stakers and DAO Modules:** Expands staking options and improves DAO treasury management.

These advancements position Lido V2 as a more adaptable, inclusive, and efficient staking solution, aligning with the broader goals of decentralization and community participation in blockchain networks.

### Node Operator Incentive Allignment

Network Operators (NOs) involved in the protocol are not obligated to put up any collateral. However, they face penalties if they fail to manage their validators effectively.

The protocol's Validator [Exit Policy](https://github.com/lidofinance/documents-and-policies/blob/7595317b8fd2ee60ab25f5cac8eac2cc2cafa149/Lido%20on%20Ethereum%20-%20Validator%20Exits%20Policy.md) outlines specific circumstances under which penalties apply. If a validator's balance falls below the set EJECTION\_BALANCE of 16 ETH or if a slashing event occurs, the validator will be forcibly exited. Additionally, NOs that do not process validator exit requests promptly will face consequences, including being barred from receiving new stake deposits and seeing a reduction of their rewards by 50%.

In extreme cases of delinquency, the DAO holds the authority to take further action. They may choose to eliminate the NO's fees completely, effectively removing them from the protocol.

## Governance

### **Governance Model and Effectiveness**

Proposals can be made by any member of the community and require a quorum to pass, ensuring decisions reflect the broader community's interests. Committees streamline operations allowing Lido to adapt and implement changes rapidly.

### **Community Strength and Engagement**

Lido DAO has cultivated a strong community presence, particularly within the Ethereum and DeFi ecosystems. This community consists of diverse stakeholders, including stakers, developers, node operators, and governance participants.

The community is not just active in discussions but also in contributions. This includes proposing improvements, participating in testnets, and providing feedback on the Lido platform.

Lido maintains transparent communication with its community, regularly updating on developments, changes, and challenges. This openness fosters trust and further engagement from the community.

### **Alignment with Bao's Values**

Lido's commitment to decentralization is evident in their governance structure, which includes community-driven decision-making processes and emergency protocols designed to prevent centralized control. However, ongoing efforts to further enhance these safeguards, as outlined in their [Decentralisation Scorecard](https://lido.fi/scorecard), indicate areas for potential improvement and vigilance.

## Architecture

### **Lido V2 system architecture**

<figure><img src="https://hackmd.io/_uploads/B1WT65EF2.png" alt=""><figcaption><p>Source: <a href="https://hackmd.io/@lido/SyagEmMwo">Lido Blog</a></p></figcaption></figure>

The Lido staking system is composed of several key components:

1. **Staking Router:** This is the central part of Lido, which manages the various staking modules. It distributes stakes among different Node Operators (NOs) and enhances the overall security of the system. Its modular design supports a variety of NOs, contributing to a more secure network. It also enables the storage of keys on Layer-2 or off-chain, providing flexible and cost-effective solutions.
2. **Deposit Security Module:** Overseen by the Deposit Security Committee, this module ensures the safety of Beacon chain deposits. It can pause deposits to prevent malicious activities. To make a deposit, signatures from two-thirds of the committee members are needed, but a single member can halt deposits. This design prevents potential collusion between committee members and NOs.
3. **Curated Node Operator Registry:** The DAO selects and manages NOs who are validators on the Beacon chain. Their addresses are stored in the NodeOperatorsRegistry contract. These operators generate unique validation keys, and Ether deposits are split and distributed among them.
4. **Withdrawals Vault:** This manages the withdrawal process of stETH, using a First-In-First-Out (FIFO) system. It operates in two modes: Turbo mode for regular operations, which accelerates withdrawal requests using available ETH, and Bunker mode for significant network disruptions, which temporarily pauses withdrawals.

### **StakingRouter Deposit Flow**

<figure><img src="https://hackmd.io/_uploads/Hy5CpqNK3.png" alt=""><figcaption><p>Source: <a href="https://hackmd.io/@lido/B1QorsoJj">Lido Blog</a></p></figcaption></figure>
