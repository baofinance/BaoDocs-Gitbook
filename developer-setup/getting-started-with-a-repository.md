# Getting started with a repository

## Introduction

Below is a standard GitHub process, for example see [https://github.com/ethereum/ethereum-org-fork/blob/dev/README.md](https://github.com/ethereum/ethereum-org-fork/blob/dev/README.md), tailored for developing in the Bao environment.&#x20;

## Fork the repository

Create yourself a GitHub username (if you don't already have one, or you might want a different username for Bao work), I'll call your new username _baorook_, below.

Log in to GitHub as &#x62;_&#x61;orook_ and go to [https://github.com/baofinance](https://github.com/baofinance), the repositories are all there. Select the repository you want to contribute to. I'll call it _repo_ below.

Go to the _repo_ and Fork it using the menu near the top - you now have a forked   branch in your personal area https://github.com/_baorook_/repo.

## Create a local copy on your computer

Your computer could be running Linux, MacOS or Windows. You could be doing development on a virtual computer (e.g. under Virtualbox)&#x20;

{% hint style="success" %}
**Ubuntu 22 on WSL2 on a Windows computer** works well and all examples will be given using this set-up.
{% endhint %}

On a terminal prompt:

$ cd _path/to/development/area_ \
$ git clone http://github.com/_baorook_/_repo baorook_/_repo_ \
$ cd _baorook_/_repo_

## Working on the local repo

For creating new files or changing existing files you can use your favourite editor.&#x20;

{% hint style="success" %}
**Visual Studio Code** is a popular choice for editor. It's especially good for those coming from a windows environment.

[https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode)&#x20;

All examples below will use it.
{% endhint %}

$ code . &

You will also need to run and debug the software for this you need to download all the dependencies.

{% hint style="success" %}
**Yarn** is a good package manager offering many benefits over npm, the native node package manager.
{% endhint %}

$ yarn install

and build the code

$ yarn hardhat compile

Read this: [https://hardhat.org/hardhat-runner/docs/getting-started#overview](https://hardhat.org/hardhat-runner/docs/getting-started#overview)

where you see npx, use yarn, e.g. "npx hardhat" => "yarn hardhat".

When you have finished pieces of work, store them in the git repository on your computer:

$ git status\
&#x20;   ... git status output ...\
$ git add \<modified or created file>\
&#x20;   ... \<more files>\
$ git commit -m"added feature XXX"

When sufficient changes are made you can push the changes into your fork in github. For that you need to install [githubCLI](https://github.com/cli/cli). Once installed,

$ gh auth login

you need to follow this rigmarole to get you authenticated on this computer to access github as password authentication is no longer supported by git.

Now push the changes back. Your local git will be connected to the github one so all you need to do is:

$ git push

Your changes are now safely in github. If your computer crashes you can always get your changes that made it to github back, so do this often.

## Getting your work into the main branch

When all your work is complete you create a pull request to have your changes reviewed by someone else on the Bao team and then incorporated into the original repository.

