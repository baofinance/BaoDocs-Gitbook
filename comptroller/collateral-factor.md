# Collateral Factor

### Collateral Factor <a href="#collateral-factor" id="collateral-factor"></a>

A cToken’s collateral factor can range from 0-90%, and represents the proportionate increase in liquidity (borrow limit) that an account receives by minting the cToken. Generally, large or liquid assets have high collateral factors, while small or illiquid assets have low collateral factors. If an asset has a 0% collateral factor, it can’t be used as collateral (or seized in liquidation), though it can still be borrowed.

Collateral factors can be increased (or decreased) through Compound Governance, as market conditions change.

**Comptroller**

```solidity
```

* `cTokenAddress`: The address of the cToken to check if listed and get the collateral factor for.
* `RETURN`: Tuple of values (isListed, collateralFactorMantissa, isComped); isListed represents whether the comptroller recognizes this cToken; collateralFactorMantissa, scaled by 1e18, is multiplied by a supply balance to determine how much value can be borrowed. The isComped boolean indicates whether or not suppliers and borrowers are distributed COMP tokens.

**Solidity**

```solidity


```

**Web3 1.0**

```js
```
