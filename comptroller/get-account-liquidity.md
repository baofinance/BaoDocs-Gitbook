# Get Account Liquidity

### Get Account Liquidity <a href="#account-liquidity" id="account-liquidity"></a>

Account Liquidity represents the USD value borrowable by a user, before it reaches liquidation. Users with a shortfall (negative liquidity) are subject to liquidation, and can’t withdraw or borrow assets until Account Liquidity is positive again.

For each market the user has [entered](https://docs.compound.finance/v2/comptroller#enter-markets) into, their supplied balance is multiplied by the market’s [collateral factor](https://docs.compound.finance/v2/comptroller#collateral-factor), and summed; borrow balances are then subtracted, to equal Account Liquidity. Borrowing an asset reduces Account Liquidity for each USD borrowed; withdrawing an asset reduces Account Liquidity by the asset’s collateral factor times each USD withdrawn.

Because the Compound Protocol exclusively uses unsigned integers, Account Liquidity returns either a surplus or shortfall.

**Comptroller**

```solidity
```

* `account`: The account whose liquidity shall be calculated.
* `RETURN`: Tuple of values (error, liquidity, shortfall). The error shall be 0 on success, otherwise an [error code](https://docs.compound.finance/v2/comptroller#error-codes). A non-zero liquidity value indicates the account has available [account liquidity](https://docs.compound.finance/v2/comptroller#account-liquidity). A non-zero shortfall value indicates the account is currently below his/her collateral requirement and is subject to liquidation. At most one of liquidity or shortfall shall be non-zero.

**Solidity**

```solidity
```

**Web3 1.0**

```js
```
