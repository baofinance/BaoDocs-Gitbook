# Command Outputs

## !15

The 15% that BAO holders own of each franchises token supply is locked in a vault, controlled by Bao holders by vote.\
\
If the community voted to set fee capture, then the 15% is staked.\
\
When the holdings of the Bao vault exceed 15% the Bao community can vote to sell off the excess they hold and distribute those fees to Bao holders via the main Bao staking mechanism.

## !amm

AMM stands for Automated Market Maker. You can read more about how AMMs work here: [https://academy.binance.com/en/articles/what-is-an-automated-market-maker-amm](https://academy.binance.com/en/articles/what-is-an-automated-market-maker-amm). \
Learn more about Impermanent loss by typing !IL in the #bot-commands chat.

## !ape

When deciding whether now is a good time to buy PNDA you need to bear in mind that people will be paying a premium over their perceived market value, to collect PNDA ahead of the start of the farming period.

There is a max supply of 100b tokens. So you can take the current price and multiply it by 100b to get the fully diluted valuation then compare that to other projects to get a sense of the market.

The circulating supply is still a tiny fraction of that, with 10m (1m pre vote) tokens scheduled to be released by Monday, dripped gradually each day and at an increased rate from 23rd April, after a vote passed due to the high premiums people were paying.

You should really only consider buying PNDA if you intend to farm with it as soon as the farms open. Even then you have to be very careful how high a premium you are paying. Once farming starts, it is expected that the premium on the price will drop as people sell rewards and bring PNDA to its fair market value.

## !apy

Some of the APYs do not display on the xDai site of Bao Finance It is a known bug and there is a baontie to pay for someone to fix it. In the mean time you can see the APYs on any of the community made sites below :

* [https://baoboard.com/](https://baoboard.com/)&#x20;
* [https://xdai.farm/](https://xdai.farm/)
* &#x20;[https://baoview.xyz/](https://baoview.xyz/)
* &#x20;[https://baostats.pythonanywhere.com/](https://baostats.pythonanywhere.com/)

## !audit

In the event that a top tier firm is now free since the last time I asked them about current schedule, and is reasonably priced I'd even consider getting one but not publicizing it, which I think is a good balance of the concerns. But, I think it'd be money poorly spent. \
\
If you walk through the code changes, which are outlined in the docs, and do a sanity check, of "if there was ever a bug what could it impact"&#x20;

The options are:

1. Referral scores.&#x20;
2. Deposit fees and withdraw fees.&#x20;

If there was an error with those then we would:&#x20;

1. Use a Graph node snapshot to solve it.&#x20;
2. Rebate the fees since they go to the dev wallet and aren't lost.&#x20;

The locking system is from Lua (which was audited from what I'm aware) and all the pool code is from Sushi (which is audited) \
\
The contract changes page in docs shows every single part of the code that wasn't audited in both contracts. [https://docs.bao.finance/contract-changes](https://docs.bao.finance/contract-changes)

## !backup

There have been some issues with cloudflare the past few days. If you experience one of these issues, the following URLs can be used as backup: [https://prod-01.bao.finance/](https://prod-01.bao.finance/) [https://prod-02.bao.finance/](https://prod-02.bao.finance/)

## !baocx

**What is BAO.cx / Is BAO.cx the same as BAO ?** \
When users migrate the $BAO token to xDAI over the bridge they receive a “$BAO on xDAI” token an ERC677 that is trustlessly controlled by the bridge contract. \
\
This means that the Bao Farm on xDAI cannot issue its own “$BAO on xDAI” and will instead issue $BAO.cx (Bao coupon xDAI) \
\
Rather than create a brand new contract just for swapping and worrying about security issues and audits, we will set up an incentivized $BAO.cx/$BAO on xDAI pool on BaoSwap that will allow users to swap between the two assets on the xDAI side. If they want to bring their Bao back onto ETH main net they will simply bring “$BAO on xDAI” back to the Omnibridge and switch back. \
\
To provide the initial liquidity for this pool, the Bao treasury will allocate 2B Bao from the liquidity pool of the treasury (currently unused) to be migrated across and staked, and will do the same with the xDAI treasury when $BAO.cx farming starts.

## !cex

Bao Finance has no plan to pay to be listed on CEX. Good centralized exchanges like FTX and Gate.io have already listed us for free. If another CEX is willing to do the same, we will be happy, but in the meantime, we will not ask, nor pay them to do so.

Bao Finance is building a product in the DeFi space and prefers to use Decentralized exchanges like SushiSwap to acquire our governance token. While it is ok to hold the governance token, we encourage our members to participate in the project we are trying to build by staking liquidity pool tokens coming from DEX like Sushiswap and contributing to the community.

## !commands

The current commands available are: !15, !amm, !ape, !apy, !audit, !backup, !baoboard, !baocx, !baoswap, !cex, !docs, !faq, !faucet, !governance, !il, !lp, !mm, !mmtokens, !panda, !pools, !rewards, !roadmap, !tokens, !tracking, !unlock, !vote, !weights, !wenfarm, !xdai

## !docs

No need to explain this one you are already here ;)

## !faq

A user from the community is suggesting that your question can be answered by reading all the aggregated information that is available in [https://docs.bao.finance/faq](https://docs.bao.finance/faq). \
\
Don't be afraid to read the docs, see common questions, read #announcements to see the latest news and follow the last proposals and ideas in [https://gov.bao.finance/](https://gov.bao.finance/) in order to have a better comprehension of what is Bao Finance and what the vision of this project is about

## !faucet

&#x20;**Where can I get 0.01 xDAI to pay for xDAI network fees**

* [https://xdai-app.herokuapp.com/faucet](https://xdai-app.herokuapp.com/faucet) (Bao Community made ! Pay it forward)&#x20;
* [https://blockscout.com/poa/xdai/faucet](https://blockscout.com/poa/xdai/faucet)
* [https://xdai-faucet.top/](https://xdai-faucet.top/)

## !governance

Governance ideas and proposal are available on our governance board which can be accessed at [https://gov.bao.finance/](https://gov.bao.finance/) \
****\
****Formal Governance votes are held on the snapshot platform at \
[https://snapshot.org/#/baovotes.eth/](https://snapshot.org/#/baovotes.eth/)

## !il

Impermanent loss is a risk that occur when providing liquidity in a pool on an AMM. Learn more here : [https://academy.binance.com/en/articles/impermanent-loss-explained](https://academy.binance.com/en/articles/impermanent-loss-explained)

## !lp

&#x20;This article explains the basics on creating LP tokens and how to stake them to farm BAO.&#x20;

* ETH main net : [https://docs.bao.finance/guides/staking-on-eth-main-net](https://docs.bao.finance/guides/staking-on-eth-main-net)&#x20;
* xDAI : [https://docs.bao.finance/guides/staking-on-xdai](https://docs.bao.finance/guides/staking-on-xdai)

## !mm

It sounds like Metamask may be having a problem. One of the following should fix it.&#x20;

1. Change ETH network then back and refresh the page
2. Clear all pending transactions in the swap page and refresh the page
3. Disable MetaMask plugin then re-enable, refresh the page&#x20;
4. Restart your browser&#x20;
5. In MetaMask go to Settings->Advanced->Reset Account
6. Reboot your computer

Alternatively, you can try those tips that worked a few times for other users

* Install a different browser (Ex: Firefox) with Metamask
* Try Metamask on mobile
* Change the RPC Node if you are on xDai within Metamask for : [https://dai.poa.network](https://dai.poa.network)

**DO NOT uninstall Metamask** unless you have a backup of your private key and / or seed phrase (12 or 24 words)

## !mmtokens

&#x20;xDAI uses different token addresses that are not the same as the contract address on mainnet. \
\
If you don't see it in your MetaMask&#x20;

1. Go to your wallet/address on [https://blockscout.com/poa/xdai/](https://blockscout.com/poa/xdai/)&#x20;
2. Click the token dropdown and select your desired token&#x20;
3. Click the MetaMask icon next to the contract address

## !panda

**PNDA token:** 0x47DcC83a14aD53Ed1f13d3CaE8AA4115f07557C0\
**Farming contract:** 0x9942cb4c6180820E6211183ab29831641F58577A

## !rewards

Your BAO doesn't become locked (as they are still pending rewards) until you harvest it or add/remove LP. When you do one of these things, 5% of your earned BAO will go to your wallet, and the other 95% will show up under your Locked BAO amount. Use !unlock command to find out how the tokens are unlocked.

## !roadmap

![](<../../.gitbook/assets/image (73).png>)

## !tokens

&#x20;If you cant see the token you want, you can use the list here to search it by contract address or add it as a custom token

* Mainnet: [https://docs.bao.finance/contracts-and-key-info/ethereum-main-net](https://docs.bao.finance/contracts-and-key-info/ethereum-main-net)&#x20;
* xDai: [https://docs.bao.finance/contracts-and-key-info/xdai](https://docs.bao.finance/contracts-and-key-info/xdai)

## !tracking

DeFi tools: **ETH main net:**

* [https://apy.vision/](https://apy.vision/)&#x20;
* [https://yai.finance/tracking](https://yai.finance/tracking)&#x20;
* [https://zapper.fi/](https://zapper.fi/)
* [https://zerion.io/](https://zerion.io/)&#x20;

**xDai:** - All community made! (use at own risk)

* [https://baoboard.com/](https://baoboard.com/) by zashton&#x20;
* [https://baoview.xyz/](https://baoview.xyz/) by vex&#x20;
* [http://bao.live/](http://bao.live/) by rfw&#x20;
* [https://xdai.farm/#/analytics](https://xdai.farm/#/analytics) by jon.almostfree&#x20;
* [https://stakedvalue.com/](https://stakedvalue.com/) by somethingElse

## !unlock

Locked BAO (Main net) will begin to be unlocked at block 13766564. \
You can check the countdown (ETH) to this block here: [https://etherscan.io/block/countdown/13766564](https://etherscan.io/block/countdown/13766564) \
\
Locked BAO.cx (xDai) will begin to be unlocked at block 20038657. \
This should be around the beginning of December 2021 where users will receive the remaining 95% of BAO or BAO.cx evenly distributed daily for 3 years.

## !vote

Currently any BAO on xDai do not count towards voting due to a technical limitation with snapshot. We will be setting up custom voting soon to fix this.

Main net votes are weighted according to the below:&#x20;

1. 33% of your locked Bao +
2. 1/4rd of your $BAO +&#x20;
3. 2x your $BAO that is in Bao/ETH Party Pool.

## !weights

The total rewards are divided by the weighting of all pools added together, then distributed to each pool according to their weighting.

A pool with a higher weight gets more rewards, but that doesn't necessarily mean a higher APY because rewards a split between everyone in the pool based on what % of the pool their liquidity represents. So a pool with twice the weighting but also twice the liquidity of a different pool, would have the same APY.

High weighted pools are less effected by additional liquidity being added.

## !wenfarm

**When will farming start on Pandaswap?**

The farming rewards will start on block #6906900. \
****Link to countdown : [https://bscscan.com/block/countdown/6906900](https://bscscan.com/block/countdown/6906900)

## !xdai

We have compiled a few infographics and tutorials to help you go through the optional xDai migration. You can find all the information you need regarding the migration here: [https://docs.bao.finance/guides/what-should-i-do-for-the-xdai-migration](https://docs.bao.finance/guides/what-should-i-do-for-the-xdai-migration)

