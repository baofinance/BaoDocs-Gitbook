---
description: This page provides a skeleton for Bao Finance's bToken minting function. WIP
---

# Mint

### Mint

The mint function transfers an asset into the protocol, earning interest based on the supply rate. The user receives bTokens equal to the supplied asset amount divided by the current exchange rate.

#### bErc20

* `msg.sender`: The account which shall supply the asset, and own the minted cTokens.
* `mintAmount`: The amount of the asset to be supplied, in units of the underlying asset.
* `RETURN`: 0 on success, otherwise an Error code Before supplying an asset, users must first approve the cToken to access their token balance.

#### bEther

* `msg.value`: The amount of ether to be supplied, in wei.
* `msg.sender`: The account which shall supply the ether, and own the minted cTokens.
* `RETURN`: No return, reverts on error.

####
