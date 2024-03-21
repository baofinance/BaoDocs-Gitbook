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

# Ecosystem Dynamics

Bao Finance provides a sophisticated ecosystem for interacting with synths and earning from liquidity incentives.

### Creating Synthetics

Minting or creating synthetic tokens can be done with one of 2 mechanisms:

#### Borrowing (shorting)

Anyone can deposit collateral and borrow a synthetic token using our Borrow Vaults. Our first synthetic tokens are baoUSD and baoETH, USD and ETH pegged tokens.

When you borrow a token using collateral, you create a short position on the borrowed token vs your collateral. \
\
For example, if you think the price of ETH will go up, you could use ETH collateral to mint baoUSD and use the baoUSD for something else or buy more ETH to leverage long on your collateral vs USD. If you think the price of ETH will go down, you can use USD collateral to borrow baoETH.&#x20;

Synths always remain fully backed because when a borrower's position becomes "at risk" due to the value of collateral falling too much compared to the loan value, anyone can repay the loan and claim the collateral plus a bonus liquidation incentive.\
\
Regardless of the price of a synthetic on any exchange, it is always worth the value its price or data feed indicates in the Borrow vault. This helps it to trade at the correct price, because borrowers can repay their loans at a discount when it is below peg or open new positions and take advantage of the premium when it is above peg.

#### Minting (longing) - COMING SOON!

Our Minter will allow anyone to swap a collateral token defined by the minter, like ETH, for a synthetic token (baoTOKEN). The value of the baoTOKEN is linked to a price/data feed and can be redeemed for the correct amount of collateral at any time.\
\
Another option the minter gives is to mint a leverage token (upTOKEN). \
\
An upTOKEN's price is based on the value of the collateral in the minter minus the value of the baoTOKENs it has minted. It is called an upTOKEN because it is a leveraged long position on the collateral in the minter. The amount of leverage is variable, increasing when the value of collateral in the system gets closer to the value of baoTOKENS, and decreasing as the value of collateral vs baoTOKENS expands.\
\
The upTOKEN can also be redeemed for the correct amount of collateral at any time. \
\
For example, a Minter that accepts ETH and mints baoUSD would also have an upETH token available for minting. \
\
If there is $1000 worth of ETH in the Minter and 500 baoUSD minted, the upETH tokens would be worth the other $500, effectively having 2x leverage on the ETH price—if the ETH value collateral increased by $500, the upETH tokens would now be worth $1000.

### Lending Synthetics - COMING SOON!

Not every collateral is suitable for backing Bao's synthetics. We are dedicated to using the most liquid and decentralized backing possible. There are many opportunities to create lending markets around our synthetics and other tokens that don't quite make the cut as collateral. \
\
A good example is sDAI, which is highly liquid but inherently centralized due to the collaterals that bao DAI. &#x20;

Lending markets are scheduled to be launched in 2024.

### Liquidity Balancers

Our liquidity balancers mint and burn synthetic tokens directly into liquidity pools. This has several benefits - there is greater control over the peg and trading fees, liquidity incentives, and arbitrages create revenue.\
\
When there is high demand for a synthetic token, the liquidity balancer can mint more tokens into the liquidity pool to bring the price back to its peg. Then, when there is less demand and the price starts to fall below peg, it can withdraw synths, rebalancing the liquidity pool\
\
Not all synthetics can have a Liquidity Balancer because minting into a liquidity pool can result in synths being backed by other assets in the liquidity pool. With this in mind, Bao is selective with the used pools. \
\
Liquidity Balancers currently mint/burn from the following pools

* baoUSD/LUSD on Balancer
* baoETH/ETH on Balancer

