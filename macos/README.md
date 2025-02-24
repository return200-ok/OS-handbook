## Get Sudoers 
sudo dseditgroup -o edit -a username -t user admin

## Install zsh
Step 1: Install Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
Step 2: Install Zsh Auto-Suggestions Plugin
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
Step 3: Install Zsh Syntax Highlighting Plugin
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
Step 4: Enable Plugins
nano ~/.zshrc
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
Step 5: Apply Changes
source ~/.zshrc


## Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## Installing Bitwarden
brew install bitwarden

## Gen SSH Key
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

## Install Telegram
brew install --cask telegram

## Install Remote Desktop Manager
brew install --cask remote-desktop-manager

## Install Microsoft Remote Desktop
brew install --cask microsoft-remote-desktop
