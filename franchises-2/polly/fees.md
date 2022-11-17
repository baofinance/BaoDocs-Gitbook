# Fees

## Nest Fees

{% hint style="info" %}
Fees for using nests are separate and in addition to the fees collected when entering or exiting a farm.
{% endhint %}

Fees for the nests will be used for a combination of burning the governance token, adding to the treasury as well as a unique reflexive payment to current nDEFI holders as a way to incentivize long-term holding. This will be achieved by distributing ⅓ of exit fees to anyone currently holding the nest token. The fees are broken down as follows:

**Entry fee 0.5%:** used to burn Polly tokens

**Annual streaming fee 1%:** accumulated by the treasury

**Exit fee 1%:** 0.66% accumulated by the treasury, 0.33% distributed to current nest holders

## Farm Fees

Fees for Polly farms will borrow the same structure as Panda and include:

* 0.75% deposit fee.

{% hint style="info" %}
Fees are block-based and not based on timestamp. As Polygon has different [average block time](https://polygonscan.com/chart/blocktime) lately, the time under each level of fee penalty may vary - the timespans are intended as a rough guideline.
{% endhint %}

| Timespan                      | Fees/Penalty | <p>Penalty expiration after first deposit<br>/ last withdraw based on block</p> |
| ----------------------------- | ------------ | ------------------------------------------------------------------------------- |
| Deposit                       | 0.75%        |                                                                                 |
| Direct withdraw in same block | 99%          |                                                                                 |
| Within 1 hour                 | 50%          | 1525                                                                            |
| Within 1 day                  | 25%          | 36600                                                                           |
| 1-3 days                      | 12%          | 109800                                                                          |
| 3-5 days                      | 8%           | 183000                                                                          |
| 5-14 days                     | 4%           | 512400                                                                          |
| 14-28 days                    | 2%           | 1024800                                                                         |
| After 28 days                 | 1%           |                                                                                 |
