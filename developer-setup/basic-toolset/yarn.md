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
$ . ~/.bashrc
$ nvm --version
```

Second install node (here we install the latest LTS version)

```
$ nvm install --lts
$ node --version
```

then, finally install yarn

```bash
$ corepack enable
```

This will cause the download the correct version of yarn for whatever project you are working in when it is first needed.

```bash
$ yarn --version
```

it is likely to give some classic version of yarn. The version of yarn actually used will be that stored in the `package.json` file in the project you are working on. For more info, see:

{% embed url="https://yarnpkg.com/getting-started/install" %}



{% hint style="warning" %}
Pay attention to yarn warnings of package conflicts. They may not cause a problem immediately but  invariably eventually do. Missing packages should be added and incorrect versions should be upgraded.
{% endhint %}

{% hint style="success" %}
update your `.gitignore` file, according to:

[https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored)


{% endhint %}
