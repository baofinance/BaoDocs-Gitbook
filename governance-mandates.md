# Governance

Bao is a living protocol, it is entirely governed by its users. The users have full governance power to change anything at any time unless they have already voted on to make something specifically unchangeable.

A number of processes and structures have been approved by the community to allow galaxy members to operate within their frameworks without having to put every spend or decision to vote.

Decisions that are not put to a public DAO vote, such as treasury breakdowns, or anything that needs sign-off from each of the Galaxies for approval shall use the Council of Guardians as a proxy.\
\
A governance forum has been created for the community in order to submit ideas and comments for the different proposals. You can find it here: [https://gov.bao.finance/](https://gov.bao.finance/) and a guide for submitting and managing a BIP [here](guides/turning-ideas-into-proposals.md)

## Frameworks

### Internal Voting

To ensure decentralization on any matter that is not subject to a full public vote, this process will create an internal voting method to ensure that no individual can wield influence over the ecosystem even as a perceived leader.

These votes will be rare, but would consist of things like:

* Disputes on internal budgeting that was already approved (i.e. revoking funds that Galaxies feel are being misused)
* Partnerships and integrations that are required to be confidential prior to launch.
* Urgent security matters (such as pulling assets out from staking when CREAM was exploited)
* Removal of a Guardian for failure to perform their duties or uphold the values of the DAO.

The internal votes will consist of:

* 1 vote representing the consensus of the Maintainer Galaxy, who should evaluate the proposal against the security of the protocol, the DAO, how it impacts the product roadmap and that it is inline with the principles of the DAO and any legality.
* 1 vote representing the Treasury, who should evaluate the proposal against any budget request, its impact on the treasury, its impact on the financial health of the protocol, and if the spend counts within existing proposals and frameworks or should have been a public vote.
* 1 vote representing the Council of Guardians who should internally vote amongst themselves and evaluate how the proposal impacts the goals of each individual galaxy as well as the overall product roadmap.
* 1 vote representing the Community Galaxy who with this vote is specifically tasked with representing the views and perspectives of the broader community and how they think a public vote on this matter would be represented.

For these internal votes, a 3/4 majority is needed for approval. A 2/2 split vote shall be considered to be a failure.

### Annual Roadmaps and Annual Election of a Maintainer Galaxy

The maintainer galaxy with each year is required to put forward a formal roadmap that includes the main focus of their year and requires them to be reelected.

Each October, any interested parties may put forward an annual proposal in a bid to be elected as the Maintainer.

On the 1st of November, each proposal shall be put to a vote.

If multiple proposals pass, the successful proposals will then be placed into a single governance vote between the successful parties to finalize the election of the new Maintainer.

If the current Maintainers are the only ones to put forward a proposal and that proposal fails they will be deemed to have been not reelected and they can try to put forward a new proposal, or the DAO can seek out new Maintainers.

Once approved any new Maintainer will take power on Jan 1st of the new calendar year, giving time for a graceful transition.

A maintainer proposal does not need to represent a single person but can represent a group who would be filling the role.

### Limiting Powers of the Maintainers over Galaxies and Guardians

Guardians once given their position by public vote (historical) or Guardian Council and multisig vote (future) will hold that position unless recalled.

Any newly elected Maintainer Galaxy may recall Guardians at the start of their leadership as long as that decision is laid out in their annual plan that is voted on.

Otherwise, Guardians will only be recalled from their position by public vote, or if they violate the agreement of operating in the DAO (such as security).

The Treasury Operations will set up annual funding for the Galaxies based on the proposals of the Guardians and the review of the Maintainer Galaxy, Treasury Galaxy, and Multisig.

Once an annual budget is granted, the treasury is obligated to pay that budget through the end of the year.

The Maintainer Galaxy has the authority to remove contract permissions, treasury permissions, multisig permissions, or repo permissions from any Galaxy member that is violating the agreement of the DAO or their position, or who is believed to be a security threat. But that will not halt the budget payments to that Galaxy.

To halt payments that were approved in an annual budget, a governance proposal must be done by public vote.

This ensures that the Maintainer Galaxy has the authority to act quickly in protecting the protocol from a security threat, but does not have the right to ‘fire’ anyone. It removes the ability for this system to be a hierarchy that does not involve a public vote. If the maintainer wanted to remove anyone from their role, it must be done so in their annual proposal that gets the majority public approval.

This payment clause will only apply to a Galaxy’s annual funding proposal that was approved by the Treasury, and would not apply to temporary Galaxies or funding that was provided to a Galaxy for a specific project.

Both temporary Galaxies and project-based funding has specific goals to hit and funding can be halted at any time if it fails to hit those goals.

Any Galaxy may be shut down, or its members recalled and payment immediately ended by full governance vote.

### BIP (BAO Improvement Proposal) Process

{% hint style="info" %}
You can find a detailed guide for creating a BIP [**here**](guides/turning-ideas-into-proposals.md)****
{% endhint %}

* There is no minimum number of BAO required to follow the steps to add a proposal
* You should develop a concept/ proposal in the [#concepts](https://gov.bao.finance/c/concepts/7) section of the forum.
* After 1 week you can request a moderator to add it to the [#governance-proposals](https://gov.bao.finance/c/governance-proposals/5) section.
* Moderators will check that the proposal has all the detail required, including any data, models, and explanations of the methodology used needed to fully assess the proposal. This is an important step that will allow “galaxy teams” to have confidence they can implement changes voted on without ambiguity or to avoid disputes resulting from miscommunication. Moderators will not filter proposals based on their views on the proposal itself, just on whether it is fully formed or not.
* The proposal should spend at least 1 week in [#governance-proposals](https://gov.bao.finance/c/governance-proposals/5), where the community can review its final wording. After 1 week unchanged, it can be moved to snapshot for a vote. This can be done by requesting moderators to inform multisig (or maintainer galaxy before multisig is implemented) that it is ready for voting.
* Multisig holders (or the maintainer galaxy before multisig is implemented) can bypass this process and put up a vote straight to snapshot where a change is deemed time-sensitive.

## Voting

Voting takes place on snapshot.page/#/bao.votes or directly via ENS on baovotes.eth

User votes are calculated by a special smart contract ( [https://etherscan.io/address/0xAed713175343D3AA83689F85Ab9E7B800a297992#code](https://etherscan.io/address/0xAed713175343D3AA83689F85Ab9E7B800a297992#code)) that counts:

1. 33% of your locked Bao +
2. 1/4th of your $BAO +
3. 3x your $BAO that is in Bao/ETH Party Pool

* Quorum requirement is 10b votes. When a vote does not receive 10b BAO voting on its outcome, it will be left to the judgement of multisig holders (or Maintainer Galaxy before multisig is implemented) on whether to implement the change or not.
* It is the responsibility of the party(s) proposing the change to promote and gather support for it in order to meet quorum
* Multisig holders (or Maintainer Galaxy, before multisig is implemented) can veto a vote. When this happens it will automatically go to a revote within 4 weeks, where 25% of voting power and a majority of 2/3 is required to overturn the veto.
* In the event of a veto, the team will create a forum post explaining their reasoning and give at least 1 week for opposition to the veto to make their points and for both sides to gather support for the revote.

{% hint style="info" %}
Vetoes are intended as a safety mechanism for multisig holders, who are voted on, to prevent changes to the project that are deemed clearly damaging to its future.
{% endhint %}

### When Community Voting is used

#### Multisig

multisig must create votes when:

* They wish to spend money outside of the treasury framework previously voted on above
* If they wish to change the cap of the Bao token, or the distribution rates.
* If they wish to change the rewards of different pools, or to add and remove new pools.
* In order to activate new features.
* To change the rules of governance, or approval percentage.&#x20;

other matters do not need to have a community vote

#### Community

The community may create votes on any matter and they will be considered binding so long as the quorums are met.

This includes the removal and replacement of the team, changes to the ecosystem, changes to rewards percentages, or distribution of the treasury.



