# Exit Vault

### Exit Market <a href="#exit-market" id="exit-market"></a>

Exit a market - it is not an error to exit a market which is not currently entered. Exited markets will not count towards account liquidity calculations.

**Comptroller**

```solidity
```

* `msg.sender`: The account which shall exit the given market.
* `cTokens`: The addresses of the cToken market to exit.
* `RETURN`: 0 on success, otherwise an [Error code](https://docs.compound.finance/v2/comptroller#error-codes).

**Solidity**

```solidity
```

**Web3 1.0**

```js


```
