---
description: how to re-use other's code
---

# Not writing code

## Git submodules

You can include in your project other's git repository. This is similar to installing a package except:

* there is no need for the owner of the code to perform any packaging, and if they do it's just a matter of creating a tag, e.g. "v0.2.6" for a given commit.
* versioning is done by branch/commit number in the other's repository.
* you can do bug fixes or enhancements locally and then push it to the other's repository

Brilliant!

{% embed url="https://www.atlassian.com/git/tutorials/git-submodule" %}
