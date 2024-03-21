# Supply Rate

At any point in time one may query the contract to get the current supply rate per block. The supply rate is derived from the borrow rate, reserve factor and the amount of total borrows.

**CErc20 / CEther**

```solidity
function supplyRatePerBlock() returns (uint)
```

* `RETURN`: The current supply rate as an unsigned integer, scaled by 1e18.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint supplyRateMantissa = cToken.supplyRatePerBlock();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const supplyRate = (await cToken.methods.supplyRatePerBlock().call()) / 1e18;
```
