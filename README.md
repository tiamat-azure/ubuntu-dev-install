# Configure Linux Elementary OS for development

![Header](img/header.png)

This project is intended to log software, libraries and frameworks installation on Linux Elementary OS.

## Install Brave browser

from : [installing-brave#linux](https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux)

```bash
sudo apt install apt-transport-https curl

curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -

source /etc/os-release

echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-${UBUNTU_CODENAME}.list

sudo apt update

sudo apt install brave-browser -y
```

## Install git

```bash
# Install git
sudo apt install git -y

# configure
git config --global user.name "Tiamat"
git config --global user.email tiamat.azure@gmail.com

# Check version
git --version
```

## Install ZSH

doc: [instaling-zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)

```bash
sudo apt install zsh

# Version check
zsh --version

# Make it your default shell
chsh -s $(which zsh)
```

## Install Oh My Zsh

Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Configure some plugins in ~/.zshrc

```bash
plugins=(
 git
 ubuntu
 docker
 history
)
```

Configure some aliases in ~/.zshrc

```bash
#======================================#
# Aliases
#======================================#

# Reload ~/.bashrc
#alias sourceb="source ~/.bashrc"
alias sourcez="source ~/.zshrc"

# Show my ip address
alias myip="curl http://ipecho.net/plain; echo"

## mkdir && cd
alias mkcd='foo(){ mkdir -p "$1"; cd "$1" }; foo '

## git
alias gac="git add . && git commit -a -m "

## npm
alias nis="npm install --save "

## VS Code
alias coden='code -n .'
alias codel='code --list-extensions'
alias codei='code --install-extension'
alias codeu='code --uninstall-extension'

## get rid of command not found ##
alias cd..='cd ..'

## a quick way to get out of current directory ##
alias ..='cd ..'
alias ...='cd ../../../'
alias ....='cd ../../../../'
alias .....='cd ../../../../'
alias .4='cd ../../../../'
alias .5='cd ../../../../..'

# handy short cuts #
alias c='clear'
alias h='history'
alias hs='history | grep'
alias j='jobs -l'

# Stop after sending count ECHO_REQUEST packets #
alias ping='ping -c 5'
# Do not wait interval 1 second, go fast #
alias fastping='ping -c 100 -s.2'

# APT commands
alias apt="sudo apt"
alias apti="sudo apt install -y"
alias aptu="sudo apt update"
alias aptui="sudo apt update && sudo apt install -y "
alias aptfu="sudo apt full-upgrade -y"
alias aptr="sudo apt auto-remove -y"

# update packages
alias apt-get="sudo apt-get"

# update on one command
alias update='sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt auto-remove'
alias updatey='sudo apt-get update --yes && sudo apt-get upgrade --yes && sudo apt-get dist-upgrade --yes && sudo apt auto-remove'
alias updatesys="sudo apt-get install unattended-upgrades"
alias updateall='sudo apt-get update --yes && sudo apt-get upgrade --yes && sudo apt-get dist-upgrade --yes && sudo apt-get install unattended-upgrades && sudo apt auto-remove'

# become root #
alias root='sudo -i'
alias su='sudo -i'

## NGINX
alias nginxreload='sudo /usr/local/nginx/sbin/nginx -s reload'
alias nginxtest='sudo /usr/local/nginx/sbin/nginx -t'

## pass options to free ##
alias meminfo='free -m -l -t'

## get top process eating memory
alias psmem='ps auxf | sort -nr -k 4'
alias psmem10='ps auxf | sort -nr -k 4 | head -10'

## get top process eating cpu ##
alias pscpu='ps auxf | sort -nr -k 3'
alias pscpu10='ps auxf | sort -nr -k 3 | head -10'

## Get server cpu info ##
alias cpuinfo='lscpu'

## set some other defaults ##
alias df='df -hPT | column -t'
alias du='du -ch'

## Date and Time Aliases
alias d='date +"%F"'
alias now='date +"%F %T"'
```

## Install VS Code

doc: [how-to-install-visual-studio-code-on-ubuntu-18-04](https://linuxize.com/post/how-to-install-visual-studio-code-on-ubuntu-18-04/)

First, update the packages index and install the dependencies by typing:

```bash
aptui software-properties-common apt-transport-https wget
```

Next, import the Microsoft GPG key using the following wget command:

```bash
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
```

And enable the Visual Studio Code repository by typing:

```bash
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
```

Install the latest version of Visual Studio Code with:

```bash
aptui code
```

Install VS Code extensions

```bash
# Install extensions
    codei shd101wyy.markdown-preview-enhanced \
&&  codei vscjava.vscode-java-pack \
&&  codei pivotal.vscode-boot-dev-pack \
&&  codei davidanson.vscode-markdownlint \
&&  codei formulahendry.docker-extension-pack

# Verify
codel
```

## Install SDKMAN

```bash
# Install
curl -s "https://get.sdkman.io" | bash

# Apply
source "$HOME/.sdkman/bin/sdkman-init.sh"

# Check version
sdk version
```

## Install JVM

Install jdk 8 (from AdopOpenJDK, Java.net and GraalVM vendors)

```bash
sdk i java 8.0.232.j9-adpt

sdk i java 8.0.232.hs-adpt

sdk i java 8.0.232-open

sdk i java 19.3.0.r11-grl
```

Verify java version

```bash
java -version
javac -version
```
