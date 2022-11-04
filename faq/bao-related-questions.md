# BAO Related Questions

## General

### What is Bao Finance?

If you are asking yourself this question, we suggest you read our docs, beginning with the [**homepage**](https://docs.bao.finance/). You will find great information about the project there.

In addition, we suggest these articles from Baoman:

* ****[**Bao V2 — The Journey**](https://thebaoman.medium.com/bao-v2-the-journey-86dab5a203de)****
* ****[**A Dumpling vs Wall St: Why we need synthetics**](https://thebaoman.medium.com/a-dumpling-vs-wall-st-why-we-need-synthetics-fb2eb87ccb86)****
* ****[**Our latest news / announcement**](https://gov.bao.finance/t/the-great-bao-migration-baoswap-co/165/66)****

### Where can I purchase the Bao Governance token?

On Ethereum main net:

* [1inch ](https://1inch.exchange/#/r/0x3bC3c8aF8CFe3dFC9bA1A57c7C3b653e3f6d6951/ETH/BAO)(This link supports the treasury)
* [Uniswap](https://app.uniswap.org/#/swap?outputCurrency=0x374cb8c27130e2c9e04f44303f3c8351b9de61c1)
* [Sushiswap](https://sushiswap.fi/swap?outputCurrency=0x374cb8c27130e2c9e04f44303f3c8351b9de61c1)
* FTX
* Gate.io
* Hotbit

On xDai :

* [BaoSwap](https://alpha.baoswap.xyz/#/swap)

### I am having trouble reaching Bao Finance, what can I do?

We faced a few times issues with our DNS provider Cloudflare that prevented some users in specific area to join Bao Finance. In those cases, we have backup sites that you can use in order to continue to interact with Bao Finance.

| Site             | Main URL                                                 | Backup site                                                                                                                                                |
| ---------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ETH Bao Finance  | [https://www.bao.finance/](https://www.bao.finance/)     | <p><a href="https://prod-01.bao.finance/">https://prod-01.bao.finance/</a> <br><a href="https://prod-02.bao.finance/">https://prod-02.bao.finance/</a></p> |
| xDai Bao Finance | [https://farms.baoswap.xyz/](https://farms.baoswap.xyz/) | [https://xdai.bao.finance/](https://xdai.bao.finance/)                                                                                                     |
| BaoSwap          | [https://alpha.baoswap.xyz/](https://alpha.baoswap.xyz/) | [https://www.baoswap.com/](https://www.baoswap.com/)                                                                                                       |

### What is BAO.cx / Is BAO.cx the same as BAO ?

When users migrate the $BAO token to xDAI over the bridge they receive a “$BAO on xDAI” token an ERC677 that is trustlessly controlled by the bridge contract.&#x20;

This means that the Bao Farm on xDAI cannot issue its own “$BAO on xDAI” and will instead issue $BAO.cx (Bao coupon xDAI)&#x20;

Rather than create a brand new contract just for swapping and worrying about security issues and audits, we will set up an incentivized $BAO.cx/$BAO on xDAI pool on BaoSwap that will allow users to swap between the two assets on the xDAI side. If they want to bring their Bao back onto ETH main net they will simply bring “$BAO on xDAI” back to the Omnibridge and switch back.&#x20;

To provide the initial liquidity for this pool, the Bao treasury will allocate 2B Bao from the liquidity pool of the treasury (currently unused) to be migrated across and staked, and will do the same with the xDAI treasury when $BAO.cx farming starts.

## Farming / Staking

### **How do I stake my liquidity to earn BAO?**

This page in the docs explains the basics on how to get started on your new farm: [https://docs.bao.finance/guides/staking-on-eth-main-net](https://docs.bao.finance/guides/staking-on-eth-main-net)

### Is it worth it for me to begin farming Bao?

Staking liquidity pool tokens in exchange of Bao tokens is the way Bao Finance distributes its governance token among the users who participate.

The decision to farm BAO tokens has many factors to consider. Before starting you should:

* Understand the risks of "Impermanent loss".
* Have a basic knowledge of AMM's, how Ethereum works, Defi in general.
* Understand the complexities & risks of being involved in a small project in it's alpha stage.
* Be willing to keep up to date with project announcements in case of an actions required.

Once you are happy with the above, the factors you should consider to decide if staking is worth for you are:

* How long you will be staking for.
* [The staking and unstaking fees](https://docs.bao.finance/fees-penalties-and-funds) and penalty fees for unstaking early.
* The APY and your expected returns over your farming period, bearing in mind:&#x20;
  * [The distribution schedule](https://docs.bao.finance/distribution-tokenomics)
  * More people can and will join your pool, bringing down the APY&#x20;
  * The [pool weighting](https://docs.bao.finance/pool-weights) and how much extra liquidity in your pool will affect the APY &#x20;
  * BAO token may change in price, which affects the APY.
* Gas prices/ fees if you are using Bao Finance on Ethereum main net.

### **My earned (pending) BAO counter is going up, but locked BAO still says 0. Why?**&#x20;

Your BAO doesn't become locked until you harvest it or add/remove LP to the same pool. When you do one of these things, 5% of your earned BAO will go to your wallet, and the other 95% will show up under your locked BAO amount.

### **When does locked BAO or BAO.cx become unlocked?**

Locked BAO (Main net) will begin to be unlocked at block 13766564. You can check the countdown (ETH) to this block here: [https://etherscan.io/block/countdown/13766564](https://etherscan.io/block/countdown/13766564) \
\
Locked BAO.cx (xDai) will begin to be unlocked at block 20038657. \
\
No matter where your Bao rewards are locked, the targeted block for unlocking will be mined around the beginning of December 2021 where users will receive the remaining 95% of BAO or BAO.cx evenly distributed daily for 3 years.

### What is the current week in the distribution schedule

[Baoboard ](https://baoboard.com/schedule)has the week distribution schedule put on a calendar to make it easy to consult that information.

## Governance

### How do governance votes and proposals work?

We are experimenting with a new process for governance with a governance message board.&#x20;

You can find it here: [https://gov.bao.finance/](https://gov.bao.finance/)&#x20;

When users want to discuss new ideas they can be placed under "**Concepts**", when the team is ready to create a governance proposal we will create a thread under "**Governance Proposal**" and users can provide feedback on the language and ask any questions.&#x20;

After that, it will finally be moved to a governance vote on Snapshot.

### **Where can I see current and past governance votes?**&#x20;

[https://snapshot.page/#/baovotes.eth/all](https://snapshot.page/#/baovotes.eth/all)
