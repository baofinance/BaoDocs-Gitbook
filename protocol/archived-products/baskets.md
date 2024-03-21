---
description: >-
  Bao Basket tokens provide low-risk, diversified automated portfolio exposure
  to crypto assets.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Baskets

{% hint style="warning" %}
Archived products have been sunset by the dao & receive no further updates - use them at your own risk.&#x20;
{% endhint %}

A [Basket](https://app.baofinance.io/baskets) token represents a group of underlying assets. Baskets give users:

* Low risk through diversification
* Automated portfolio management
* Improved capital efficiency

Baskets reduce gas fees, impermanent loss, and tax events. V1 focuses on community-governed baskets. Governance controls composition, rebalancing, and yield strategies.

Future versions will enable custom user baskets with customizable rebalancing and yield farming.

### Issuing Baskets

When issuing new Baskets, deposited tokens buy the underlying assets. These deposits go into yield farms, then the yield-bearing tokens get deposited into a vault.

Issuing requests over-collateralization to allow for slippage. Unused deposits are returned. Baskets reflect performance of underlying token values and yields.

### Redeeming

Redeeming Baskets returns the proportional share of underlying tokens. Users can choose to redeem into the original asset and sell underlying tokens.

### Pricing

Baskets are backed by the underlying token values. Divergence from underlying value creates arbitrage opportunities.

If Basket price > underlying value, issue more Baskets, sell for profit.

If Basket price < underlying value, buy Baskets, redeem for profit.
