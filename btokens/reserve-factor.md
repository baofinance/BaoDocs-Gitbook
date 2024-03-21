# Reserve Factor

### Reserve Factor <a href="#reserve-factor" id="reserve-factor"></a>

The reserve factor defines the portion of borrower interest that is converted into reserves.

**CErc20 / CEther**

```solidity
function reserveFactorMantissa() returns (uint)
```

* `RETURN`: The current reserve factor as an unsigned integer, scaled by 1e18.

**Solidity**

```solidity
CErc20 cToken = CToken(0x3FDA...);
uint reserveFactorMantissa = cToken.reserveFactorMantissa();
```

**Web3 1.0**

```js
const cToken = CEther.at(0x3FDB...);
const reserveFactor = (await cToken.methods.reserveFactorMantissa().call()) / 1e18;
```
