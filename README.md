# OSX environment setup
The purpose of this repository is to describe an installation of a new OSX environment with all the needed "goodies" for a kick ass environment.

## XCode
1. Install XCode from the app store.
* Install the command line tools from XCode installations (This will install git for example..).

## Clone repository
1. Create the ```Developments``` directory:
```shell
cd ~
mkdir ./Developments
cd ./Developments
```
* Clone the repository:
```shell
git clone https://github.com/kazazor/env-setup
```

## Homebrew
1. Go to [this](http://brew.sh/) link and install the package manager for OSX.
* Lets add more formulas to our brew installer:
```shell
brew tap hombrew/versions
```
* Now lets update homebrew with all the newest formulas:
```shell
brew update
brew doctor
```

## Node.js
###  Installation
1. Using ```brew``` we'll search for the latest stable (LTS) version of node.js:
```shell
brew search node
```
* And then install it (at the time of writing the LTS version is 4.3.0):
```shell
brew install homebrew/versions/node4-lts
```

### Global packages
```shell
sudo npm i -g gulp
sudo npm i -g yo
```

## Git settings + auto complete
### Aliases + Auto complete
1. Edit the ~/.bash_profile file
* Add the following rows
```shell
# Git
source ~/Developments/env-setup/bash/env
source ~/Developments/env-setup/bash/git
source ~/Developments/env-setup/git/alias
```
* Load the aliases in the open terminal (for new terminals it will be set already):
```shell
source ~/.bash_profile
```
4. Create a symlink to the .gitconfig file:
```shell
ln -s ~/Developments/env-setup/git/.gitconfig ~/.gitconfig
```

### Configuration
1. Change your global git configuration:
```shell
git config --global user.name “<my full name>”
git config --global user.email “<my email>”
```
* Update the ```push.default``` behavior on your machine:
```shell
git config --global push.default nothing
```
(What does this configuration do? Basically it forces you to specify on which branch you would like to push the code, so you won't accidentally push the code to master or any other branch. This settings is being done in order to avoid mistakes for those of us working with git from the command line. It will not effect SourceTree or alike tools.. For more info go [here](http://stackoverflow.com/questions/8170558/git-push-set-target-for-branch )).

## Atom editor
1. Download [Atom](https://atom.io/)
* Install the **Atom Shell Commands** from the settings.
* Change the **Preferred line length** to 120.
* Change the **Tab Length** to 2.
* Install the following packages from the package manager:
```Shell
apm install autoprefixer
apm install docblockr
apm install linter
apm install linter-csslint
apm install trailing-spaces
```
* Install packages that could only be installed from the Atom interface:
  * https://atom.io/packages/emmet
  * https://atom.io/packages/javascript-snippets
  * https://atom.io/packages/todo-show

## Useful apps
### App Store
1. Fly cut
* Go2Shell

### Outsiders
1. App Cleaner - https://freemacsoft.net/appcleaner/
* Spectacle - https://www.spectacleapp.com/
