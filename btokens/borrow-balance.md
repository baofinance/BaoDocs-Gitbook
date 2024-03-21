# Borrow Balance

A user who borrows assets from the protocol is subject to accumulated interest based on the current borrow rate. Interest is accumulated every block and integrations may use this function to obtain the current value of a user’s borrow balance with interest.

**CErc20 / CEther**

```solidity
function borrowBalanceCurrent(address account) returns (uint)
```

* `account`: The account which borrowed the assets.
* `RETURN`: The user’s current borrow balance (with interest) in units of the underlying asset.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint borrows = cToken.borrowBalanceCurrent(msg.caller);
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const borrows = await cToken.methods.borrowBalanceCurrent(account).call();
```

### Borrow Rate <a href="#borrow-rate" id="borrow-rate"></a>

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
