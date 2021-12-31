# Installing Python 

## Mac

> We recommend to install Zsh first of all, which is a powerful CLI framework with tons of available plugins to improve productivity while working in the terminal: https://ohmyz.sh. We are using it and all the videos are done with Zsh as a default terminal shell.

Install Homebrew first -- https://brew.sh

In MacOS Terminal run 

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Then install `pyenv` to manage Python environments (we want to keep original Python version installed with your MacOS). This tool will manage multiple versions of Python and is described as "simple, unobtrusive, and follows the Unix tradition of single-purpose tools that do one thing well."

In the Terminal run

`brew install python `

> The version number, like 3.10.1 below, is representing the latest version available, please check https://www.python.org/downloads/ to see the current version at the moment of when you are going to do it and replace 3.10.1 here with the current latest version.

Now check where python is installed:

`ls -l /usr/local/bin/python*`

And create a symbolic link with 

`ln -s -f ../Cellar/python@3.10/3.10.1/bin/python3.10 /usr/local/bin/python`

Now we can check the version of Python installed with 

`python -V`

It should return

`Python 3.10.1`

Now to start Python environment run `python` in the Terminal.

Done! 👍

---

<!-- > More info about pyenv: https://realpython.com/intro-to-pyenv/ -->

## Windows

1. Go to https://www.python.org/downloads/windows/

2. Click on the link for the Latest Python 3 Release (3.10.1 at the moment of writing this doc)

3. Choose the Windows x86-64 executable installer and save it in your Downloads directory

4. Run the installer from Windows Explorer

	In the Installer check "Add Python 3.10 to Path" check box

	Click Customize installation where "All Optional Features" should be checked 

	Click "Next" button

5. Check "Install for all users"

6. Click "Install"

	When prompted, allow the installer to modify your system

Once installed restart your laptop and open GitBash.

To check the installed version run `python -V` in GitBash. The output should be `Python 3.10.1`. 

Now to start Python environment run `python` in GitBash.

Done! 👍


