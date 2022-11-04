# RHINO Questions

### What is the purpose of RHINO ?

As the goal with Bao products has always been to incentivize long term stakers and robust liquidity, the community noted the need for ways to incentivize long term locked liquidity that has strong incentives for using it long term, but penalties for removing it, to create stability in the ecosystem.

### Why is 12% taken on every transaction?

We followed the story of the token Safemoon. While this project itself is not good nor have a good use case, it used some interesting concepts in managing liquidity.

We had been following the code, and the projects it was based on for a while before the project even got famous to evaluate liquidity lockup incentives, and worked on our own fork that makes improvements to the Safemoon model to remove the ponzi elements and bad code, while keeping locked liquidity rewards.

The catch is that Rhino trades incur a 12% penalty.

* Of that 6% is added to the LP as permanent locked liquidity.
* Another 6% is distributed back to Rhino holders.

### Will the transaction feed always be 12% ?

No. The fee will diminish over time.

Please see the [Rhino section](https://docs.bao.finance/franchises/panda/items-and-creatures/creatures#8766) for a detailed breakdown

### How is the transaction fees distributed ?

The 12% taken on each transaction consists out of a 6% liquidity fee and 6% tax fee portion.

The liquidity fee will be seeded to the PandaSwap RHINO-BNB LP pool. LP pools created on other swaps on BSC will not receive anything from this portion.

The tax fee will be seeded to all RHINO holders on BSC which have not been excluded from rewards, all LP pools will receive rewards.

Current address which have been excluded temporarily, to increase rewards to other users:

* Burn address (0x000000000000000000000000000000000000dead)
* Dev address (0x9B3D5b1A191DBa87fF2F158E681BAfCc4371b6Ab)
* Bao community address (0x609991ca0Ae39BC4EAF2669976237296D40C2F31)
* Swapper address (0x745c8E1c0315162C33408454b48E53C9F178eB68)

### How do I obtain RHINO?

RHINO can be acquired for PNDA tokens by the following methods.

* In [**PandaSwap Farms**](https://farms.pandaswap.xyz/rhino) using the 1:1 PNDA to RHINO contract. There will be a 2% Contract fee to use this contract on top of the 12% Transaction fee that occur on every RHINO transaction.
* In [**PandaSwap AMM**](https://www.pandaswap.xyz/#/swap) or PancakeSwap. You will need to set your slippage to at least 13% to be able to swap successfully on these exchanges.

### I have the error INSUFFICIENT\_OUTPUT\_AMOUNT when I try to swap for RHINO. Why ?

This error occurs when you haven't set the slippage tolerance to at least 13%

![](<../../.gitbook/assets/image (58).png>)

### When do I receive my RHINO rewards?

Reflexive rewards are only updated if you’ve made a transaction and there has been a distribution.&#x20;

Depending on the wallet it might take a while for the synchronization to show your rewards. In other cases you need to do a transaction or even manually poll the contract.

