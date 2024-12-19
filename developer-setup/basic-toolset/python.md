---
description: Python is used by some tools.
---

# Python

As Python is comes with Ubuntu by default so all that remains is to check this

```bash
$ python3 --version
$ pip --version
```

we need poetry (python's equivalent of node's npm or yarn). It's used in bao-base, for example.

```
$ sudo apt install python3-poetry
$ poetry --version
```



```bash
$ sudo apt install pipx
$ pipx --version
$ pipx ensurepath
$ . ~/.bashrc
```

pipx allows python packages, such as slither, to be installed.
