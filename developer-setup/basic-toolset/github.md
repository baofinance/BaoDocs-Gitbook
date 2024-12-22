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

### Running github actions locally

The following allows you to run the same scripts that the github CI runs, but locally.&#x20;

```json
gh extension install https://github.com/nektos/gh-act
```

You also need docker to do this

```bash
$ sudo apt-get update
$ sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$ sudo apt-get update
$ sudo apt-get install -y docker-ce
```

now check the docker installation

```bash
$ docker --version
$ sudo systemctl status docker
```

if the docker status isn't right

```bash
$ sudo systemctl start docker
$ sudo systemctl enable docker
$ sudo systemctl status docker
```

finally enable yourself to do stuff on it

```bash
$ sudo usermod -aG docker $USER
$ newgrp docker
```

Finally, to have docker work like github actions you need a passwordless sudo for certain commands, note that these lines also remove the password for those commands, which isn't ideal:

```bash
$ echo "$USER ALL=(ALL) NOPASSWD:$(which apt)" | sudo tee -a /etc/sudoers.d/$USER
$ echo "$USER ALL=(ALL) NOPASSWD:$(which apt-get)" | sudo tee -a /etc/sudoers.d/$USER
$ echo "$USER ALL=(ALL) NOPASSWD:$(which add-apt-repository)" | sudo tee -a /etc/sudoers.d/$USER
$ sudo chmod 0440 /etc/sudoers.d/$USER
```
