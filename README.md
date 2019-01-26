# Awesome-BriteCore

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

BriteCore is a suite of web software that runs an insurance company. We're a
remote-first organization, where nearly every employee works remotely, and we've
been that way since the beginning.

We use modern technology that is ever-evolving, because that's how technology
works. In order for our employees, business partners, and clients to be able
to keep up with our technology, we decided to put this Awesome List together.
We hope you find it useful!

## Contents
- [Development Environment](#development-environment)
    - [Make bash consistent](#make-bash-consistent)
    - [Install base tools](#install-base-tools)
        - [Xcode](#xcode)
        - [HomeBrew](#homebrew)
        - [Git](#git)
    - [Setting up Python](#setting-up-python)
- [Design](#design)
- [Web Development](#web-development)
- [Infrastructure](#infrastructure)

## Development Environment
Our company develops almost exclusively on mac laptops, so this is currently
geared toward that. Over the last 15 years we've tried just about everything
you can imagine, but we like dead-simple now. The less we have to maintain on
a development environment, the more software we get to build.

### Make bash consistent
Update your `.bash_profile` to source `.bashrc`:
```
if [ -r ~/.bashrc ]; then
   source ~/.bashrc
fi
```

Then make a new `.bashrc` file if you don't have one already:
```
touch ~/.bashrc
```

Now you can make any bash changes directly in `~/.bashrc` from now on, and
that's the only place you need to make changes.

These are the first lines I added to my `~/.bashrc` file:

```
# Infinite Bash History
HISTSIZE=
HISTFILESIZE=

# Better Prompt
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\] $ "

# Terminal Colors
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```

### Install base tools

#### Xcode ####
```
xcode-select --install
```

#### Homebrew ####
[Install Homebrew](https://brew.sh/)

#### Git ####
```
brew install git
```
- [Create SSH keypair](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
- [Add public ssh key to GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

If you want to see what branch you have checked out in your bash prompt, then
add this to the top of your `~/.bashrc` file:
```
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
```

And modify your `export PS1` line to read:
```
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$(parse_git_branch)\[\033[00m\] $ "
```

### Setting up Python

This was a great guide that we used as we created our specific steps which are below
[The definitive guide to setup my Python workspace by Henrique Bastos](https://medium.com/@henriquebastos/the-definitive-guide-to-setup-my-python-workspace-628d68552e14)

```
brew install pyenv
brew install pyenv-virtualenv
brew install pyenv-virtualenvwrapper
```

Then add this to your `.bashrc` file:
```
# directory that contains the virtualenvs of all projects
export WORKON_HOME=~/.virtualenvs
# directory that contains the projects
export PROJECT_HOME=~/projects

# enable pyenv
eval "$(pyenv init -)"

# enable pyenv virtualenvwrapper plugin
pyenv virtualenvwrapper_lazy

# Enable auto-activation of pyenv-virtualenv
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```

## Design

## Web Development
