# Node based build/test

#### npm

This is the default package manager used for node packages.

It works for most cases in practice but hits problems hence, ...

#### yarn

Yarn is a package manager designed as a replacement for npm. It is faster, more secure and more robust.

[https://yarnpkg.com/getting-started/install](https://yarnpkg.com/getting-started/install)

Make sure you are using a version of yarn > 2. Yarn 1 is great but yarn 2 offers a path to zero installs, even if we don't use them just yet (baby steps).&#x20;

{% hint style="warning" %}
Pay attention to yarn warnings of package conflicts. They may not cause a problem immediately but  invariably eventually do. Missing packages should be added and incorrect versions should be upgraded.
{% endhint %}

#### Hardhat

Hardhat does testing with node, so your test files can be either javascript or typescript.

{% embed url="https://hardhat.org/docs" %}

$ yarn hardhat build

$ yarn hardhat test

$ yarn hardhat coverage
