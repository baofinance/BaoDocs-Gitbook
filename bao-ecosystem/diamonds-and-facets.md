# Diamonds and Facets

## What are they?

Basically a way of writing contracts that can be upgraded while maintaining a single contract address. Hint: it uses delegate\_call a lot under the hood.

Here's a well written spec that's fairly easy to follow:

{% embed url="https://eips.ethereum.org/EIPS/eip-2535" %}
Nick Mudge ([@mudgen](https://github.com/mudgen)), "ERC-2535: Diamonds, Multi-Facet Proxy," _Ethereum Improvement Proposals_, no. 2535, February 2020. \[Online serial]. Available: https://eips.ethereum.org/EIPS/eip-2535.
{% endembed %}

More:

*   Detail on the implementations, see [https://github.com/mudgen/diamond](https://github.com/mudgen/diamond)

    TODO: find out which implementation (if any of those) that Bao uses.
* Related documents/blogs/etc. [https://github.com/mudgen/awesome-diamonds](https://github.com/mudgen/awesome-diamonds)

Because they add an additional layer of indirection (that's what allows them to be upgraded) it makes it much more difficult to understand the relationships between different contracts.

They, therefore, need to be documented.

## Where are they used?

Not enough, lol. Or maybe too much.

### Baskets

A basket is a Diamond

<img alt="" class="gitbook-drawing">
