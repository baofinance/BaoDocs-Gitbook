# Total Reserves

Reserves are an accounting entry in each cToken contract that represents a portion of historical interest set aside as cash which can be withdrawn or transferred through the protocol’s governance. A small portion of borrower interest accrues into the protocol, determined by the reserve factor.

**CErc20 / CEther**

```solidity
function totalReserves() returns (uint)
```

* `RETURN`: The total amount of reserves held in the market.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint reserves = cToken.totalReserves();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const reserves = (await cToken.methods.totalReserves().call());
```
