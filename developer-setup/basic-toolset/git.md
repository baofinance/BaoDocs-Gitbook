# Git

Git is software that manages a local repository for your code changes.

{% embed url="https://git-scm.com/docs/user-manual" %}
Git user manual
{% endembed %}

## Installation

{% tabs %}
{% tab title="Ubuntu" %}
```bash
$ sudo apt install git
```
{% endtab %}

{% tab title="macOS" %}
probably use brew
{% endtab %}

{% tab title="Windows" %}
```powershell
> winget install -e 'Git'
```
{% endtab %}
{% endtabs %}

## Setup

You should now let git know your name and email so that your wonderful code can be properly attributed to you.

```bash
$ git config --global user.name "My name"
$ git config --global user.email "my@email.address"
```

Your `.gitconfig` file in your home directory has now been updated.

These can be set up on a repository-by-repository basis by going to the top level directory of the repository and running the commands without the `--global`.

