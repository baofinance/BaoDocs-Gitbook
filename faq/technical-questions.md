# Technical Questions

## Wallet / Metamask

### **Bao Finance or BaoSwap isn't functioning as it should**

You may have one or more of the following issues :&#x20;

* APY are not loading
* Transactions are stuck pending for more than 10 minutes
* Transactions are not found on Blockscout or Etherscan
* You cannot connect your wallet to one of our site
* Other similar problems&#x20;

Those issues are usually a symptom of a problem with Metamask itself. You can usually fix it by using one of the solution below:

* Restarting your browser
* Switch ETH networks and back.
* In MetaMask go to Settings->Advanced->Reset Account
* Disable/re-enable the meta mask plugin

### How do I add the xDai network in Metamask?

All you need is to follow this [tutorial](https://www.xdaichain.com/for-users/wallets/metamask/metamask-setup).

### **I can't see my BAO / BAO.cx in Metamask, how can I add it?**&#x20;

In Metamask, scroll down to the bottom of assets and click "add token", then "custom token".

Input these token address depending of the token and network you are currently :

* BAO (ETH) : 0x374CB8C27130E2c9E04F44303f3c8351B9De61C1
* BAO (xDai) : 0x82dFe19164729949fD66Da1a37BC70dD6c4746ce
* BAO.cx (xDai) : 0xe0d0b1DBbCF3dd5CAc67edaf9243863Fd70745DA

Another way on xDai to add a token to a wallet is to :

1. Go to your wallet/address on [https://blockscout.com/poa/xdai/](https://blockscout.com/poa/xdai/)&#x20;
2. Click the token dropdown and select your desired token&#x20;
3. Click the MetaMask icon next to the contract address

## Omnibridge / xDai network

### **Can I bridge ETH to xDai ?**

No, the omnibridge works only with ERC20 tokens. wETH is an ERC20, you can bridge that instead.

### What are my options for bridging liquidity to xDai?&#x20;

1. Acquire xDai by bridging DAI using the [**xDai Bridge**](https://bridge.xdaichain.com/) or buying it with fiat. You can find more details on how to do both [**here**](../guides/staking-on-xdai/bridge-dai-to-xdai-for-gas-fees.md)****
2. Bridge ERC20 tokens using the[ **OmniBridge**](https://omni.xdaichain.com/)**.** You can find more help in the guide [**here**](../guides/staking-on-xdai/bridge-assets-to-xdai.md)****

## ETH Main Net

### Why are gas fees so high?

Main net fees are high but if your gas fee is much higher than you expect it could be due to a problem cause by having too little ETH in your wallet.\
\
_The deposit transaction will use roughly 198,730 gas._

_It will estimate the fee at around 298,095 gas as a precaution for gas limit._

_The withdraw transaction takes 124,809 gas if you are in the shorted bracket, and estimates 209,713 gas._

_If you have less ETH than (gasprice \* gas estimate) then the estimate breaks and continues to show higher numbers._
