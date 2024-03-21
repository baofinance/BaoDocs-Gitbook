# Enter Vault

### Enter Markets <a href="#enter-markets" id="enter-markets"></a>

Enter into a list of markets - it is not an error to enter the same market more than once. In order to supply collateral or borrow in a market, it must be entered first.\


**Comptroller**

```solidity
```

* `msg.sender`: The account which shall enter the given markets.
* `cTokens`: The addresses of the cToken markets to enter.
*   `RETURN`: For each market, returns an error code indicating whether or not it was entered. Each is 0 on success, otherwise an [Error code](https://docs.compound.finance/v2/comptroller#error-codes).\


    **Solidity**

    ```solidity
    ```

    **Web3 1.0**

    ```js
    ```
