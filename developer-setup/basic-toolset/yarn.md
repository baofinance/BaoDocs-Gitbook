---
description: dependency manager and script orchestrator
---

# Yarn

It's a bit convoluted to install yarn. The steps are:

* install the node version manager (nvm)
* use nvm to install node
* use facilities that come with node to install and select the correct version of yarn

First get nvm as per [https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)

```bash
$ wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

Second&#x20;

then, finally install yarn according to their instructions:

{% embed url="https://yarnpkg.com/getting-started/install" %}

$ yarn --version

Make sure you are using a version of yarn > 2. Yarn 1 is great but yarn 2 offers a path to zero installs, even if we don't use them just yet (baby steps).&#x20;

{% hint style="warning" %}
Pay attention to yarn warnings of package conflicts. They may not cause a problem immediately but  invariably eventually do. Missing packages should be added and incorrect versions should be upgraded.
{% endhint %}
