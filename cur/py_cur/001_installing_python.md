# Installing Python on Mac

> We recommend to install Zsh first of all, which is a powerfull CLI framework with tons of available plugins to improve productivity while working in the terminal: https://ohmyz.sh. We are using it and all the videos are done with Zsh as a default terminal shell.

Install Homebrew first -- https://brew.sh

In MacOS Terminal run 

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Then install `pyenv` to manage Python environments (we want to keep original Python version isntalled with your MacOS). This tool will manage multiple versions of Python and is described as "simple, unobtrusive, and follows the Unix tradition of single-purpose tools that do one thing well."

In the Terminal run

`brew install pyenv `

> The version number, like 3.9.1 below, is representing the latest version available, please check https://www.python.org/downloads/ to see the current version at the moment of when you are going to do it and replace 3.9.1 here with the current latest version.

Then run 

`pyenv install 3.9.1`

And then assign this version to be default one with running

`pyenv global 3.9.1`

And create a symbolic link with 

`echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc`

Now we can check the version of Python installed with 

`python -V`

It should return

`Python 3.7.7`

Done! 👍

---
## Extra resources

- More info about pyenv: https://realpython.com/intro-to-pyenv/
