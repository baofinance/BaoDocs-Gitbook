---
description: >-
  A guide for moving your LP tokens staked on the ETH main net to xDAI and
  staking them
---

# Move Staked LPs to xDAI

{% hint style="warning" %}
BAO farming  on xDai has ended on June 2nd 2021. Moving Sushi LP to xDai should not be done anymore.
{% endhint %}

{% hint style="info" %}
Moving LP tokens to xDAI is optional. Main net pools will remain operational and supported.
{% endhint %}

There will be no UNI LP pools that can be staked on xDAI, just SUSHI LP and BaoSwap LP. If you are in a UNI pool and want to move to xDAI you will have to identify whether a pool for your assets is available on SUSHI or BaoSwap then follow instructions based on the available xDAI pool.

#### Identifying which xDAI pools are available for migrating UNI LP

* Browse to [https://xdai.bao.finance](https://xdai.bao.finance).
* Find a pool with the same assets you want to stake.
* Follow The instructions below based on what pool is available for you.

## SUSHI pool available

* **Unstake** your LP tokens from your main net pool

![](<../../.gitbook/assets/image (107).png>)

* **If your LP tokens are SLP tokens, skip to the next step**. If your LP tokens are from UNI then you need to migrate liquidity to SUSHI using the SUSHI migrate tool: [https://lite.sushiswap.fi/#/migrate](https://lite.sushiswap.fi/#/migrate)
  * Connect your wallet
  * Select the pool you want to migrate from **Your Uniswap Liquidity**
  * select the amount of LP tokens you want to migrate in **Amount of Tokens**
  * click **Migrate Liquidity**&#x20;

![](<../../.gitbook/assets/image (21).png>)

{% hint style="info" %}
Before you click on the link to follow xDai's bridging instructions, take note of the bullet points below - They may come in handy.
{% endhint %}

* Bridge your LP tokens to the xDAI chain by following the guide here: [https://docs.tokenbridge.net/eth-xdai-amb-bridge/multi-token-extension/ui-to-transfer-tokens/transfer-erc20](https://docs.tokenbridge.net/eth-xdai-amb-bridge/multi-token-extension/ui-to-transfer-tokens/transfer-erc20)
  *   When you **unlock** the token you wish to transfer you can specify the amount of tokens to unlock or give unlimited approval. If you plan to bridge more at a later date it might be preferable to use an **Infinite Unlock**, to save gas in the future.&#x20;

      * Click **settings** in the top right
      * Flick the **Infinite Unlock** switch

      ![](<../../.gitbook/assets/image (26).png>)


  * When selecting the token to migrate, you may have to add the LP token as a custom token.
    * Find the **SUSHI** **LP Pair Contract** address and copy it from: [https://docs.bao.finance/contracts-and-key-info](https://docs.bao.finance/contracts-and-key-info)
    * Select  **Add Custom Token**, paste the contract address, then click **Add Token** & continue with the xDAI guide linked above.

![](<../../.gitbook/assets/image (50).png>)

![](<../../.gitbook/assets/image (82).png>)

* Follow the guide to [**Stake on xDai.bao.finance**](stake-on-xdai.bao.finance.md)****

## BaoSwap pool available

*   **Unstake** your LP tokens from your main net pool



![](<../../.gitbook/assets/image (101).png>)

* To begin removing liquidity from UNI go to [https://app.uniswap.org/#/pool](https://app.uniswap.org/#/pool) and select the pool.
  * If it doesn't appear, you need to import it:
    * Click the **Import it** link
    * Copy and paste the **Token Contract address** to the search box from [https://docs.bao.finance/contracts-and-key-info](https://docs.bao.finance/contracts-and-key-info) and select the token

![](<../../.gitbook/assets/image (16).png>)

![](<../../.gitbook/assets/image (88).png>)

* Choose the amount to remove and approve the transactions.
* Follow the guide for bridging your tokens to xDAI: [https://docs.tokenbridge.net/eth-xdai-amb-bridge/multi-token-extension/ui-to-transfer-tokens/transfer-erc20](https://docs.tokenbridge.net/eth-xdai-amb-bridge/multi-token-extension/ui-to-transfer-tokens/transfer-erc20)
  * If you don't see a token, You may have to add it as a custom token. Select **Add Custom Token**, then paste the **Token Contract** address from [https://docs.bao.finance/contracts-and-key-info](https://docs.bao.finance/contracts-and-key-info), then **add token**.
  *   When you **unlock** the token you wish to transfer, remember you will have to unlock again when you have bridged the amount you specify. If you plan to move more at a later date, take that into account.



      ![](<../../.gitbook/assets/image (50).png>)

      ![](<../../.gitbook/assets/image (82).png>)
* Follow the guide to **** [**Add Liquidity to BaoSwap**](add-liquidity-to-baoswap.md)****
