# Exchange Rate

Each cToken is convertible into an ever increasing quantity of the underlying asset, as interest accrues in the market. The exchange rate between a cToken and the underlying asset is equal to:

```solidity
exchangeRate = (getCash() + totalBorrows() - totalReserves()) / totalSupply()
```

**CErc20 / CEther**

```solidity
function exchangeRateCurrent() returns (uint)
```

* `RETURN`: The current exchange rate as an unsigned integer, scaled by 1 \* 10^(18 - 8 + Underlying Token Decimals).

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint exchangeRateMantissa = cToken.exchangeRateCurrent();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const exchangeRate = (await cToken.methods.exchangeRateCurrent().call()) / 1e18;
```

Tip: note the use of `call` vs. `send` to invoke the function from off-chain without incurring gas costs.
