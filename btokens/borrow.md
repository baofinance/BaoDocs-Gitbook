# Borrow

The borrow function transfers an asset from the protocol to the user, and creates a borrow balance which begins accumulating interest based on the Borrow Rate for the asset. The amount borrowed must be less than the user’s Account Liquidity and the market’s available liquidity. To borrow Ether, the borrower must be ‘payable’ (solidity).

**CErc20 / CEther**

```solidity
```

* `msg.sender`: The account to which borrowed funds shall be transferred.
* `borrowAmount` : The amount of the underlying asset to be borrowed.
* `RETURN`: 0 on success, otherwise an Error code

**Solidity**

```solidity
```

**Web3 1.0**

```js
```
