---
description: >-
  This will be an explanation on liquidations and how you can avoid them while
  using Bao Markets.
---

# Liquidations

Liquidations occur when you go over your Debt Limit. Health Factor shows you how close you are to possibly being liquidated.\
\
A health factor of 2 means your collateral can half in price before you are flagged for liquidation. 3 means it can lose 66% of its value and 4 means 75% etc.

![](<../../.gitbook/assets/image (13).png>)

Under 1 means that you have gone over your debt limit - Your position is flagged for liquidation and any liquidation bots watching can immediately repay your loan and seize the equivalent value in collateral + a liquidation penalty. \
\
It's important to take price volatility into account when making when minting synthetics, for both collateral and the synthetics.

The formula is as follows USD Supplied \* ACF / USD Minted.

USD Supplied represents the total value of the assets you have designated as collateral

ACF is your Average Collateral Factor, you can find the Collateral factor in the tabs of the assets you supplied. And then take the average of all of them together.

USD Minted is the amount of synths you minted using your collateral.
