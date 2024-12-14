---
description: How to install, setup and use version control software.
---

# Version Control

## Git

Git is software that manages a local repository for your code changes

{% embed url="https://git-scm.com/docs/user-manual" %}
Git user manual
{% endembed %}

From a windows prompt:

```powershell
> winget install -e 'Git'
```

From a linux prompt:

```bash
$ sudo apt install git
```

You should now let git know your name and email so that your wonderful code can be properly attributed.

```bash
$ git config --global user.name "My name"
$ git config --global user.name "my@email.address"
```

Your `.gitconfig` file in your home directory has now been updated.

These can be set up on a repository-by-repository basis by going to the top level directory of the repository and running the commands without the `--global`.

## GitHub

GitHub is a service where all your code should end up. GitHub also acts as a backup for your code changes so use it frequently.

{% embed url="https://cli.github.com/manual/" %}

install gh on Ubuntu using:

```bash
$ sudo apt install gh
```

The next step is to allow github to be accessed via git. Run this:

```bash
$ gh auth login
```

and answer its prompts:

* what account? <mark style="color:blue;">GitHub.com</mark>
* preferred protocol? <mark style="color:blue;">HHTPS</mark>
* authenticate GitHub CLI? <mark style="color:blue;">Login with a web browser</mark>

then follow the instructions on screen and in the browser.

Finally

```bash
$ gh auth setup-git
```

Your `.gitconfig` file in your home directory has now been updated with the authentication method.

You can now call commands in git that interact with git hub, such as `git clone`, `git pull`, etc.&#x20;
