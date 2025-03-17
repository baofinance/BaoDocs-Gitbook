---
description: Useful links for installing various tools
---

# Additional Tools



## Yarn CLI completions

### Ubuntu

```bash
# Install yarn bash completion if not already installed
curl -o ~/.yarn-completion https://raw.githubusercontent.com/dsifford/yarn-completion/master/yarn-completion.bash

# Add to your .bashrc
echo "source ~/.yarn-completion" >> ~/.bashrc
source ~/.bashrc
```

### MacOs

```bash
# If using oh-my-zsh, enable the yarn plugin in ~/.zshrc
plugins=(... yarn ...)

# Or manually add completion
mkdir -p ~/.zsh/completion
curl -o ~/.zsh/completion/_yarn https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/plugins/yarn/_yarn
echo 'fpath=(~/.zsh/completion $fpath)' >> ~/.zshrc
echo 'autoload -Uz compinit && compinit' >> ~/.zshrc
source ~/.zshrc
```

## Chrome browser

Ubuntu comes with Firefox installed and that works well but Chrome has additional features for those that use the Google infrastructure, like sharing extensions (thinking metamask, etc.).

{% embed url="https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu" %}

## Toggl time tracker

If you're paid by the hour this timer helps count it.

{% embed url="https://track.toggl.com/timer" %}

