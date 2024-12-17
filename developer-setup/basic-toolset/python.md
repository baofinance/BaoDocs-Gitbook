---
description: Python is used by some tools
---

# Python

As Python3 is comes with Ubuntu by default so all that remains is to install the python3 package manager, pipx. First check python is installed:

```bash
$ python3 --version
```

then install the package manager and fix up the path.

```bash
$ sudo apt install pipx
$ pipx --version
$ pipx ensurepath
$ . ~/.bashrc
```

pipx allows python packages, such as slither, to be installed.
