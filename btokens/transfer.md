# Transfer

### Transfer <a href="#transfer" id="transfer"></a>

Transfer is an ERC-20 method that allows accounts to send tokens to other Ethereum addresses. A cToken transfer will fail if the account has entered that cToken market and the transfer would have put the account into a state of negative liquidity.

**CErc20 / CEther**

```solidity
function transfer(address recipient, uint256 amount) returns (bool)
```

* `recipient`: The transfer recipient address.
* `amount`: The amount of cTokens to transfer.
* `RETURN`: Returns a boolean value indicating whether or not the operation succeeded.

**Solidity**

```solidity
CEther cToken = CEther(0x3FDB...);
cToken.transfer(0xABCD..., 100000000000);
```

**Web3 1.0**

```js
const cToken = CErc20.at(0x3FDA...);
await cToken.methods.transfer(0xABCD..., 100000000000).send({from: 0xSender});
```
