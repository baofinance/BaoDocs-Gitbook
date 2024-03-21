# Get Cash

Cash is the amount of underlying balance owned by this cToken contract. One may query the total amount of cash currently available to this market.

**CErc20 / CEther**

```solidity
function getCash() returns (uint)
```

* `RETURN`: The quantity of underlying asset owned by the contract.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint cash = cToken.getCash();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const cash = (await cToken.methods.getCash().call());
```
