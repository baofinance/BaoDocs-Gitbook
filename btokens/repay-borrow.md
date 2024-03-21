# Repay Borrow

The repay function transfers an asset into the protocol, reducing the user’s borrow balance.

**CErc20**

```solidity
```

* `msg.sender`: The account which borrowed the asset, and shall repay the borrow.
* `repayAmount`: The amount of the underlying borrowed asset to be repaid. A value of -1 (i.e. `2^256` - 1) can be used to repay the full amount.
* `RETURN`: 0 on success, otherwise an Error code Before repaying an asset, users must first approve the cToken to access their token balance.

**CEther**

```solidity
```

* `msg.value`: The amount of ether to be repaid, in wei.
* `msg.sender`: The account which borrowed the asset, and shall repay the borrow.
* `RETURN`: No return, reverts on error.

**Solidity**

```solidity
```

**Web3 1.0**

```js
```
