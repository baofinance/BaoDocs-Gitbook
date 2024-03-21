---
description: WIP
---

# Introduction

The Comptroller is the risk management layer of the Bao Finance protocol. It determines collateral requirements and liquidation conditions for each user. The Comptroller approves or denies transactions when a user interacts with a bToken.

The Comptroller maps user balances to prices (via the Oracle) and assigned risk weights called Collateral Factors. Rather than users picking assets, the DAO proposes and approves allowed collateral through governance.

Collateral Factors are tuned through governance to balance risk versus usability for borrowers. By quantifying and limiting individual risk, the Comptroller provides guarantees needed for uncorrelated lending across assets.
