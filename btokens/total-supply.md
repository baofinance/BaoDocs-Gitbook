# Total Supply

Total Supply is the number of tokens currently in circulation in this cToken market. It is part of the EIP-20 interface of the cToken contract.

**CErc20 / CEther**

```solidity
function totalSupply() returns (uint)
```

* `RETURN`: The total number of tokens in circulation for the market.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint tokens = cToken.totalSupply();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const tokens = (await cToken.methods.totalSupply().call());
```

### Underlying Balance <a href="#underlying-balance" id="underlying-balance"></a>

The user’s underlying balance, representing their assets in the protocol, is equal to the user’s cToken balance multiplied by the [Exchange Rate](https://docs.compound.finance/v2/ctokens/#exchange-rate).

**CErc20 / CEther**

```solidity
function balanceOfUnderlying(address account) returns (uint)
```

* `account`: The account to get the underlying balance of.
* `RETURN`: The amount of underlying currently owned by the account.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint tokens = cToken.balanceOfUnderlying(msg.caller);
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const tokens = await cToken.methods.balanceOfUnderlying(account).call();
```
