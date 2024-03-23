# Solidity



## Coding style

When writing code you should follow the guidelines here:

* https://www.rareskills.io/post/solidity-style-guide
* https://docs.soliditylang.org/en/latest/style-guide.html

## Openzeppelin library

Openzeppelin provide a library of useful base contracts.

## Upgradeable contracts

Most new contract code should be written to sit behind a proxy as this allows it to be upgraded. OpenZeppelin have migrated their upgradeable library to use UUPS proxies

{% embed url="https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable" %}

{% embed url="https://forum.openzeppelin.com/t/uups-proxies-tutorial-solidity-javascript/7786" %}

This is written for Hardhat but the solidity code is the same for hardhat or foundry.

## Namespace storage

Namespace storage allows data to be shared between the proxy contract and the logic contracts

{% embed url="https://eips.ethereum.org/EIPS/eip-7201" %}

we use the namespace identifier bao.storage.\<contract name>
