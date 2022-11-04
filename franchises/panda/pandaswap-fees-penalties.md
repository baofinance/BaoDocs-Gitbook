# Fees, Penalties & Funds

{% hint style="warning" %}
**PNDA will unlock 5% of harvested tokens. The remaining 95% are locked.** Those tokens will lock until BSC block [**15513277**](https://bscscan.com/block/countdown/15513277), and will unlock in a linear fashion until block [**68079942**](https://bscscan.com/block/countdown/68079942) (roughly 6 years from the beginning of emissions).
{% endhint %}

Bao's community of projects has always been about long-term product vision. In Bao, we saw more short-term farmers than expected despite implementing penalty fees. As such, we have increased the penalty withdrawal curve for PNDA so it should be less profitable for short-term farmers.

All fees go into the treasury that backs PandaSwap. The treasury funds are owned by the users who vote on their allocation and use.\
\
These fees only apply to deposited/staked assets and not to the harvesting of  PNDA rewards

#### Deposit

* A 0.75% deposit fee.

#### Withdrawal

{% hint style="warning" %}
The slashing fee gets reset when you withdraw.\
The slashing fee is based on either the first deposit or most recent withdrawal time
{% endhint %}

{% hint style="warning" %}
Fees are based on the number of blocks and the Estimated Timespan is based on a 3 seconds block time. If block times vary then so will the timespan of each fee
{% endhint %}

| Estimated Timespan            | Fees/Penalty | <p>Penalty expiration after first deposit<br> / last withdraw based on block</p> |
| ----------------------------- | ------------ | -------------------------------------------------------------------------------- |
| Deposit                       | 0.75%        |                                                                                  |
| Direct withdraw in same block | 99%          |                                                                                  |
| Within 1 hour                 | 50%          | 1200                                                                             |
| Within 1 day                  | 25%          | 28800                                                                            |
| 1-3 days                      | 12%          | 86400                                                                            |
| 3-5 days                      | 8%           | 144000                                                                           |
| 5-14 days                     | 4%           | 403200                                                                           |
| 14-28 days                    | 2%           | 806400                                                                           |
| After 28 days                 | 0.1%         |                                                                                  |

