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
npm i -g ntl
```

### NVM
Install ```nvm``` using the instructions [here](https://github.com/creationix/nvm).

Then, install the node version you would like to have using:
```shell
nvm install <version>
```

In order to use the new version instead of your system version you could run ```nvm list``` to see all the versions you've installed, and then use the specific version:
```shell
nvm use <version>
```

<a name="nvm_bash_profile"></a>In order to activate NVM for all the terminal windows you'll open in the future you'll need to add to the ```~/.bash_profile``` file the following section:
```shell
# NVM
# Start nvm in the new session
export NVM_DIR="/Users/orkazaz/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm

# Showing what version of node is being used
export NVM_NODE_CURRENT=$(nvm current);
echo "#################################"
echo "Using Node version: $NVM_NODE_CURRENT";
echo "#################################"
```

In order to load it for all the existing terminals, you'll need to run this command:
```shell
source ~/.bash_profile
```

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

## Git settings + auto complete
### Aliases + Auto complete
1 - Edit the ```~/.bash_profile``` file<br>
2 - Add the following rows
```shell
# Git
source ~/Developments/env-setup/bash/env
source ~/Developments/env-setup/bash/git
source ~/Developments/env-setup/git/alias
```
3 - Load the aliases in the open terminal (for new terminals it will be set already):
```shell
source ~/.bash_profile
```
4 - Create a symlink to the .gitconfig file:
```shell
ln -s ~/Developments/env-setup/git/.gitconfig ~/.gitconfig
```

### Configuration
1. Change your global git configuration:
```shell
git config --global user.name "<my full name>"
git config --global user.email "<my email>"
git config --global core.editor "atom"
```
* Update the ```push.default``` behavior on your machine:
```shell
git config --global push.default nothing
```
(What does this configuration do? Basically it forces you to specify on which branch you would like to push the code, so you won't accidentally push the code to master or any other branch. This settings is being done in order to avoid mistakes for those of us working with git from the command line. It will not effect SourceTree or alike tools.. For more info go [here](http://stackoverflow.com/questions/8170558/git-push-set-target-for-branch )).

## Useful apps
### App Store
1. FlyCut

### Outsiders
1. [App Cleaner](https://freemacsoft.net/appcleaner/)
* [Spectacle](https://www.spectacleapp.com/)
* [Go2Shell](http://zipzapmac.com/go2shell)

## Troubleshooting
### NVM
When opening a new terminal window (after performing [this step](#nvm_bash_profile)), you might get this error:
```shell
N/A version x.x.x is not installed yet
```

Why is this hapening?<br>
You might have an alias for a node version you uninstalled / doesn't exists. Like described in thie [github issue](https://github.com/creationix/nvm/issues/437#issuecomment-46477874).<br>
In order to fix that, just change the alias to point to a new node version you do have install. For example:
```
nvm alias default 4.4.4
```
