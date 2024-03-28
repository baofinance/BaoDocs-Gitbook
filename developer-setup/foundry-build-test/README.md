# Foundry build/test

### Foundry

Foundry is a replacement for hardhat but doesn't use node for testing. Instead it uses Solidity and has it's own EVM (ethereum virtual machine) running. This vastly simplifies test code (no conversion from and to, for example, `uint256` and `ethers.bignumber`).&#x20;

The downside is that it's the new guy on the block and so, for example, the documentation is sparse, the console output is clunky, there's no `string.concat` (at least until version 0.8.12 of the compiler) and vscode debugging doesn't exist yet.

{% embed url="https://book.getfoundry.sh/" %}

{% hint style="warning" %}
In foundry, the version of solidity is taken from the `pragma solidity` spec in a file and a matching version found in `~/.svm`.

This generally works but can fail if the pragma specifies a specific version, e.g.&#x20;

<pre class="language-solidity"><code class="lang-solidity"><strong>pragma solidity 0.7.1;
</strong></code></pre>

and you don't have exactly `~/.svm/0.7.1`

if you have, say, `~/.svm/0.7.6` then as 0.7.6 is supposed to be a bugfix version of 0.7.5, etc. then forge will use it, but it will then complain that it's using the wrong version. It's as if the `pragma solidity 0.7.1;` is being interpreted as `pragma solidity ^0.7.1;`

You should generally always add a `^`, or a `>=` when you use `pragma solidity`or you will eventually run into these conflicts unless, of course, if your code only works with a specific version of the compiler which is unlikely.
{% endhint %}

## Dependencies / Packages

In foundry you don't use yarn or npm, basically because there are no node files!

You add solidity dependencies / packages using

$ forge install \<package>

See [https://soliditydeveloper.com/foundry](https://soliditydeveloper.com/foundry) for an example of how to use it with OpenZeppelin.

More on foundry with OpenZeppelin upgradeable contracts:

{% embed url="https://docs.openzeppelin.com/upgrades-plugins/1.x/foundry-upgrades" %}

## Testing



### Code coverage

{% embed url="https://medium.com/@rohanzarathustra/forge-coverage-overview-744d967e112f" %}
