---
description: >-
  This page provides a skeleton for Bao Finance's redeem underlying function.
  WIP
---

# Redeem underlying

The redeem underlying function converts bTokens into a specified amount of the underlying asset and transfers it to the user. The bTokens redeemed equals the amount received divided by the current exchange rate. Redemptions must be below account liquidity and market availability.\
\


**CErc20 / CEther**

```solidity
```

* `msg.sender`: The account to which redeemed funds shall be transferred.
* `redeemAmount`: The amount of underlying to be redeemed.
* `RETURN`: 0 on success, otherwise an Error code

**Solidity**

```solidity
```

**Web3 1.0**

```js
```
