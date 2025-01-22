---
description: Python is used by some tools.
---

# Python

As Python is comes with Ubuntu by default so all that remains is to check this

```bash
$ python3 --version
$ pip --version
```

in case we need to install different versions of python (e.g. slither doesn't work with python3.12 which is the version installed with ubuntu 24.04 LTS.

```bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
```

New versions of python can now be installed

```bash
sudo apt install python3.13 python3.13-dev
```

We also need [poetry ](https://python-poetry.org/docs/)(python's equivalent of node's npm or yarn). It's used in bao-base, for example. We _don't_ use the command `sudo apt install python3-poetry` because in older versions of ubuntu this installs an earlier version of poetry that doesn't support a feature we rely on (e.g.`--directory`). Instead we do:

```bash
$ curl -sSL https://install.python-poetry.org | python3 - --version 1.8.5
```

we _don't_ install the latest version because from version 2.0.0, it is currently broken.

ensure your `~/.bashrc` has

```bash
export PATH="$HOME/.local/bin:$PATH"
```

then run

```bash
$ . ~/.bashrc
$ poetry --version
```
