# Liquidation Incentive

The additional collateral given to liquidators as an incentive to perform liquidation of underwater accounts. A portion of this is given to the collateral cToken reserves as determined by the seize share. The seize share is assumed to be 0 if the cToken does not have a `protocolSeizeShareMantissa` constant. For example, if the liquidation incentive is 1.08, and the collateral’s seize share is 1.028, liquidators receive an extra 5.2% of the borrower’s collateral for every unit they close, and the remaining 2.8% is added to the cToken’s reserves.

**Comptroller**

```solidity
function liquidationIncentiveMantissa() view returns (uint)
```

* `RETURN`: The liquidationIncentive, scaled by 1e18, is multiplied by the closed borrow amount from the liquidator to determine how much collateral can be seized.

**Solidity**

```solidity
Comptroller troll = Comptroller(0xABCD...);
uint closeFactor = troll.liquidationIncentiveMantissa();
```

**Web3 1.0**

```js
const troll = Comptroller.at(0xABCD...);
const closeFactor = await troll.methods.liquidationIncentiveMantissa().call();
```
