# Repay Borrow Behalf

The repay function transfers an asset into the protocol, reducing the target user’s borrow balance.

**CErc20**

```solidity
function repayBorrowBehalf(address borrower, uint repayAmount) returns (uint)
```

* `msg.sender`: The account which shall repay the borrow.
* `borrower`: The account which borrowed the asset to be repaid.
* `repayAmount`: The amount of the underlying borrowed asset to be repaid. A value of -1 (i.e. `2^256` - 1) can be used to repay the full amount.
* `RETURN`: 0 on success, otherwise an Error code Before repaying an asset, users must first approve the cToken to access their token balance.

**CEther**

```solidity
function repayBorrowBehalf(address borrower) payable
```

* `msg.value`: The amount of ether to be repaid, in wei.
* `msg.sender`: The account which shall repay the borrow.
* `borrower`: The account which borrowed the asset to be repaid.
* `RETURN`: No return, reverts on error.

**Solidity**

```solidity
CEther cToken = CEther(0x3FDB...);
require(cToken.repayBorrowBehalf.value(100)(0xBorrower) == 0, "transfer approved?");
```

**Web3 1.0**

```js
const cToken = CErc20.at(0x3FDA...);
await cToken.methods.repayBorrowBehalf(0xBorrower, 10000).send({from: 0xPayer});
```
