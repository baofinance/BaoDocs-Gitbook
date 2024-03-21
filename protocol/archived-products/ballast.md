---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Ballast

{% hint style="warning" %}
Archived products have been sunset by the dao & receive no further updates - use them at your own risk.&#x20;
{% endhint %}

The Ballast provides a stable swap mechanism between synthetic and non-synthetic asset pairs. Users can seamlessly swap between:

* baoUSD ↔ LUSD
* baoETH ↔ ETH

Assets used to mint synthetics are held in reserve by the Ballast contract, reinforcing price stability.

#### Fee Structure

* 1% swap fee between baoUSD ↔ LUSD
* 1% swap fee between baoETH ↔ ETH

#### Price Stability

The fees incentivize prices to hover within 1% of the pegged rate. Larger deviations on exchanges create arbitrage opportunities between Ballast and external prices.\


Ballast provides confidence that users can repay synths near their pegged value, even if external prices fluctuate. This adds reliability for the entire Bao ecosystem.
