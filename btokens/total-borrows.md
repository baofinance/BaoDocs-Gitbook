# Total Borrows

Total Borrows is the amount of underlying currently loaned out by the market, and the amount upon which interest is accumulated to suppliers of the market.

**CErc20 / CEther**

```solidity
function totalBorrowsCurrent() returns (uint)
```

* `RETURN`: The total amount of borrowed underlying, with interest.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint borrows = cToken.totalBorrowsCurrent();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const borrows = (await cToken.methods.totalBorrowsCurrent().call());
```
