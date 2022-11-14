# Locked Token Distribution

Locked Bao holders have three options they can take with their locked positions. Any distribution will only begin once manually initiated by the wallet owner, then follow the option/s selected below:

1. &#x20;Choose to lock your balance directly into voting escrow BAO (veBAO) for a minimum of 3 years (the length of the unlock period). After you choose to lock into veBAO, you will no longer be able to participate in the streaming of liquid BAOv2 tokens, as all the tokens from your distribution will be converted to a locked veBAO balance. Locking into veBAO relinquishes access to your tokens as they will be locked, but you will benefit from having veBAO. veBAO gives ownership of a percentage of protocol fees and the ability to vote on governance proposals, as well as boosting liquidity rewards by up to 2.5x. Tokens locked into veBAO will not be subject to any slashing penalty.
2. &#x20;Choose to perform a liquid distribution over three years. Over the three years, 100% of your locked tokens will be distributed to you along the distribution curve defined below. Users can claim (this costs gas) as often as they would like throughout this distribution, as long as they have accrued more tokens since their last claim. All tokens claimed using this method are not subject to any slashing penalty.
3. &#x20;Users that perform a liquid distribution can choose to end their distribution early at any time after the distribution starts. A significant slash penalty will be applied to the tokens unlocked early, while all tokens already unlocked have no slash applied. The slash is based on the function defined below. Choosing this option will end your distribution and immediately send the remaining tokens (minus slash) to your wallet. To activate this option, the user has to start their distribution manually, then at some point afterward, decide to end it early.

The protocol will collect all the slashed balances from users ending their distributions early. The community can agree on how the collected slash fees should be used, potentially including future incentives for veBAO holders, liquidity providers, product users, etc.

**Distribution Function**

X in this piecewise function below is the number of days (the end being the 1095th day, AKA 3 years)\
![](broken-reference)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>A graph showing how BAO will unlock over time</p></figcaption></figure>

The function is designed to weight distribution towards the end, so those who wait longer are rewarded more. Any function that does not have a bias to the end of the three years will incentivize holders to slash early and sell the tokens rather than continue participating in the DAO/vote escrow system.

**Proposed Slash Function**

X is days since the start of distribution

0 <= X <= 365 || (100 -.01369863013x) (starts at 100% slash and approaches 95% slash)

365 < X <= 1095 || 95 constant (constant at 95% slash)

The slash function starts at the same date the address selects to start their BAO distribution. The slash function begins at 100% on day 0 and approaches a constant 95% slash on day 365 and after that. On the day the user ends their distribution early (3rd option), the slash function defines how much of their remaining distribution will be slashed. The user will immediately receive the remainder of this percentage of their remaining distribution.

Putting the distribution and the slash function together

<figure><img src="https://global.discourse-cdn.com/standard10/uploads/bao/original/1X/d0683e4c31a1d5cbfdf4a1a23f76325ca884ee43.gif" alt=""><figcaption></figcaption></figure>

In the graph above, the blue points are the state of both curves, respectively. The orange point is the percentage of their total distribution that the user can claim if they choose to end their distribution at that point.\
\
