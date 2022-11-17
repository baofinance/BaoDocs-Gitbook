# Panda as Bao's Sandbox

Many people asked, that since our main goal is to build synthetics with LP assets from partners like Sushi on xDAI, why are we spending time on Panda?

There are two causes:

1. We want our synths to be accessible across chains. To be on many chains, a synth needs strong liquidity pools on different chains to support liquidations.
2. We needed a testing ground for experimenting with new mechanisms and products.

We had decided not to build our synths on the main Ethereum network right now as it is just too expensive for users, and so we migrated to xDAI and linked Bao to xDAI using our Bao.cx coupon.

This meant anything we do on xDAI impacts the mainnet tokenomics for Bao, and so it didn’t make sense to make risky experiments.

But, as we started to design synths, it became clear that a lot of the economics for making robust multi-collateral synthetics were theoretical and not things that have been tested in real environments by teams.

We saw a lot of unexpected behaviors in how users used the initial Bao Finance farms, which were designed so we could monitor liquidity behavior for the synth protocol. But this means we need to do the same sort of testing for other features.

That is part of why in the design proposal for Panda, Baoman suggested the franchise model.

Panda on BSC sits on its own chain and has its own governance token. The Bao community owns a portion of that token locked in a vault and has governance control over it.

If Panda is successful, then the Bao community prospers from the experiments both in new technologies but also potential value flowing back into the Bao ecosystem.

If Panda has glitches, failures, bugs, or problematic code in new features though, it is separate enough that it doesn’t harm the main Bao ecosystem.

For this reason, we can view the Panda ecosystem as the sandbox for Bao. This means we can move much quicker, launch experimental features, try new features faster and experiment with parameters and riskier models on Panda before bringing them to Bao.

This means we expect PNDA, Pandaswap, Panda Farms, and any sub-projects or features launched on BSC to be much higher risk, quicker changing, and more experimental than regular Bao products. They should be treated as if they are always a high-risk alpha/beta experiment and not assumed to be stable.

While we’ll still have a governance process for Panda, we’ll also make an accelerated proposal model for proposals to be deployed more quickly into the Panda ecosystem and give elected community representatives (currently called “Core team and external teams”) a bit more room to make quick changes and deploys in this ecosystem compared to Bao.

On Bao’s ecosystem, we have been one of the projects that move slowly with caution and security. Our community thinks that is important, especially in a decentralized project run by anonymous team members. We’ll continue to have this practice of best in class security and planning on Bao, while letting Panda be like our crazy cousin off to explore the wild west.\
\\

![](https://miro.medium.com/max/2436/1\*N7uD7XbIbZLnC-\_VC5-8wg.jpeg)
