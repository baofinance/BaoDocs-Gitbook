# Borrow Rate

At any point in time one may query the contract to get the current borrow rate per block.

**CErc20 / CEther**

```solidity
function borrowRatePerBlock() returns (uint)
```

* `RETURN`: The current borrow rate as an unsigned integer, scaled by 1e18.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint borrowRateMantissa = cToken.borrowRatePerBlock();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const borrowRate = (await cToken.methods.borrowRatePerBlock().call()) / 1e18;
```
