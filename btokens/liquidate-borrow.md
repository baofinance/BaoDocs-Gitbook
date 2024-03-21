# Liquidate Borrow

A user who has negative account liquidity is subject to liquidation by other users of the protocol to return his/her account liquidity back to positive (i.e. above the collateral requirement). When a liquidation occurs, a liquidator may repay some or all of an outstanding borrow on behalf of a borrower and in return receive a discounted amount of collateral held by the borrower; this discount is defined as the liquidation incentive. A liquidator may close up to a certain fixed percentage (i.e. close factor) of any individual outstanding borrow of the underwater account. Unlike in v1, liquidators must interact with each cToken contract in which they wish to repay a borrow and seize another asset as collateral. When collateral is seized, the liquidator is transferred cTokens, which they may redeem the same as if they had supplied the asset themselves. Users must approve each cToken contract before calling liquidate (i.e. on the borrowed asset which they are repaying), as they are transferring funds into the contract.

**CErc20**

```solidity
function liquidateBorrow(address borrower, uint amount, address collateral) returns (uint)
```

* `msg.sender`: The account which shall liquidate the borrower by repaying their debt and seizing their collateral.
* `borrower`: The account with negative account liquidity that shall be liquidated.
* `repayAmount`: The amount of the borrowed asset to be repaid and converted into collateral, specified in units of the underlying borrowed asset.
* `cTokenCollateral`: The address of the cToken currently held as collateral by a borrower, that the liquidator shall seize.
* `RETURN`: 0 on success, otherwise an Error code Before supplying an asset, users must first approve the cToken to access their token balance.

**CEther**

```solidity
function liquidateBorrow(address borrower, address cTokenCollateral) payable
```

* `msg.value`: The amount of ether to be repaid and converted into collateral, in wei.
* `msg.sender`: The account which shall liquidate the borrower by repaying their debt and seizing their collateral.
* `borrower`: The account with negative account liquidity that shall be liquidated.
* `cTokenCollateral`: The address of the cToken currently held as collateral by a borrower, that the liquidator shall seize.
* `RETURN`: No return, reverts on error.

**Solidity**

```solidity
CEther cToken = CEther(0x3FDB...);
CErc20 cTokenCollateral = CErc20(0x3FDA...);
require(cToken.liquidateBorrow.value(100)(0xBorrower, cTokenCollateral) == 0, "borrower underwater??");
```

**Web3 1.0**

```js
const cToken = CErc20.at(0x3FDA...);
const cTokenCollateral = CEther.at(0x3FDB...);
await cToken.methods.liquidateBorrow(0xBorrower, 33, cTokenCollateral).send({from: 0xLiquidator});
```
