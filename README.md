# Initial development environment for Mac OS

This document describes how I have set up my developer environment on a new MacBook. 

I have setup mainly for 
- Node 
- Python 
- Mobile Application development on android & iOS using React Native
- ASP.NET Core

As you read and follow these steps, feel free to send me any feedback or comments you may have.

The document assumes you are new to Mac. The steps below were tested on OS X High Sierra.

- System Update (#system-update)
- Install developer browsers(#install-web-browsers)
- ITerm2

## System Update 

First thing you need to do, on any OS actually, is update the system! For that: Apple Icon > Software Update

## Install Web Browsers 

I use both chrome and firefox. I need chrome for any react native development and firefox for all the web development and testing

So go ahead and grab both of them. 

If you are a newbie like me to Mac and don't know how to install an application, then just drag and drop the app to Applications.

## ITerm2 
Lot of work happens only on terminal. ITerm2 [https://www.iterm2.com/] is a nice terminal which has loads of capabalities. Go ahead and install it.

## VS Code
I prefer working on VSCode. Donwload and install VSCode from https://code.visualstudio.com/

## Homebrew

Package managers make it so much easier to install and update applications (for Operating Systems) or libraries (for programming languages). The most popular one for OS X is Homebrew.

### Install XCode Command line utilities
An important dependency before Homebrew can work is the Command Line Tools for Xcode. These include compilers that will allow you to build things from source.

    $ xcode-select --install

### Install Homebrew
    
    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

One thing we need to do is tell the system to use programs installed by Hombrew (in /usr/local/bin) rather than the OS default if it exists. We do this by adding /usr/local/bin to your $PATH environment variable:

    $ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile

Close and re-open the command prompt

Check if there are no issues with Homebrew

    $ brew doctor




## Git

    $ brew install git

when done check 

    $ git --version

also test,

    $ which git

the output must be /usr/local/bin/git


## Python

OS X, like Linux, ships with Python already installed. But you don't want to mess with the system Python (some system tools rely on it, etc.), so we'll install our own version with Homebrew. It will also allow us to get the very latest version of Python 2.7.

The following command will install Python 2.7 and any dependencies required (it can take a few minutes to build everything):

    $ brew install python

When finished, you should get a summary in the terminal. Running $ which python should output /usr/local/bin/python.

$ pip install --upgrade distribute
$ pip install --upgrade pip

Executable scripts from Python packages you install will be put in /usr/local/share/python, so let's add it to the $PATH. To do so, we'll create a .path text file in the home directory (I've already set up .bash_profile to call this file):

    $ cd ~
    $ subl .path

And add these lines to .path:

    PATH=/usr/local/share/python:$PATH
    export PATH

Save the file and open a new terminal to take the new $PATH into account (everytime you open a terminal, .bash_profile gets loaded).


## Virtualenv

Virtualenv is a tool that creates an isolated Python environment for each of your projects. For a particular project, instead of installing required packages globally, it is best to install them in an isolated folder in the project (say a folder named venv), that will be managed by virtualenv.

The advantage is that different projects might require different versions of packages, and it would be hard to manage that if you install packages globally. It also allows you to keep your global /usr/local/lib/python2.7/site-packages folder clean, containing only critical or big packages that you always need (like IPython, Numpy).

### Install 

To install virtualenv, simply run:

    $ pip install virtualenv

## Node

Install Node.Js from Homebrew

    $ brew update
    $ brew install node

## MongoDB

### Install

    $ brew update
    $ brew install mongo

### Running mongodb as a launch service

    ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist

### Install management studio for MongoDB
Install any of the mongodb management studios. I prefer to use Studio3T


## Projects Folder

This really depends. I put all my version controlled projects under ~/workspace. 
Other documents I have, or things not yet under version control, I like to put in ~/Dropbox (if you have Dropbox installed), or ~/Documents.