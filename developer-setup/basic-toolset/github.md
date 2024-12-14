# GitHub

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
