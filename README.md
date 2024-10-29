# Linux for Development Debian/WSL
## Installing WSL
+ Open powershell as admin
  ```
  wsl – -install
  ```
+ Reboot
  ```
  Restart-Computer
  ```
  
## Essentials
+ Open Debian/WSL and access root
  ```
  cd /
  ```
+ Update & Upgrade
  ```
  sudo apt update && sudo apt upgade
  ```
+ Install main dependencies
  ```
  sudo apt install git curl wget git p7zip-full build-essential python3 python-is-python3 libfuse2
  ```
+ Video
  ```
  sudo apt-get install ubuntu-restricted-extras gstreamer1.0-plugins-ugly
  ```

## Zsh & Oh-My-Zsh
+ zsh
  ```
  sudo apt install zsh zsh-doc
  ```
+ Set Zsh as default Shell
  ```
  chsh -s $(which zsh)
  ```

+ Oh-My-Zsh
  ```
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
  ```
+ Close and Open Terminal again
+ Choose `2` "Populate..."

## asdf - SDK version manager
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.1
```

## Terminal Upgrades
+ Editors
  ```
  sudo apt-get install -f micro bat
  ```
+ Eza
  + Dependencies
    ```
    sudo apt install -f gpg
    ```
    
  + Installation
    ```
    sudo mkdir -p /etc/apt/keyrings
    wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
    echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
    sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
    sudo apt update
    sudo apt install -y eza
    ```

## Zsh plugins
### Installations
+ zsh-syntax-highlighting
  ```
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
  ```
+ zsh-autosuggestions
  ```
   git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
  ```  

+ zsh-fast-syntax-highlighting
  ```
  git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
  ```

+ zsh-autocomplete
  ```
  git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
  ```

+ zsh-bat
  ```
  git clone https://github.com/fdellwing/zsh-bat.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-bat
  ```

+ zsh-eza
  ```
  git clone https://github.com/z-shell/zsh-eza.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-eza
  ```

### Enable Plugins  
+ Open zsh config file
  ```
  sudo micro ~/.zshrc  
  ```
+ Search for `ZSH_THEME`
  ```
  ZSH_THEME="jonathan"
  ```  
+ Search for `plugins`
  ```
  plugins=(git ubuntu extract asdf zsh-eza command-not-found colored-man-pages pip pipenv gradle spring gulp grunt npm yarn ng dotenv composer laravel docker docker-compose zsh-syntax-highlighting zsh-autosuggestions fast-syntax-highlighting zsh-autocomplete)
  ```

### Making aliases 
+ Eza
  ```
  # 'eza' parameters definition
  eza_params=('--git' '--icons' '--classify' '--group-directories-first' '--time-style=long-iso' '--group' '--color-scale')
  
  # 'ls' commands aliases and variants using 'eza'
  alias ls='eza $eza_params'
  alias l='eza --git-ignore $eza_params'
  alias ll='eza --all --header --long $eza_params'
  alias llm='eza --all --header --long --sort=modified $eza_params'
  alias la='eza -lbhHigUmuSa'
  alias lx='eza -lbhHigUmuSa@'
  alias lt='eza --tree $eza_params'
  alias tree='eza --tree $eza_params'
  
  # Enable auto list directories on cd
  export AUTOCD=1
  ```
+ Bat
  ```
   # 'Bat' aliases
   alias cat="batcat"
   alias bat="batcat"
  ```
+ Save and Quit
+ Source it
  ```
  source ~/.zshrc
  ```

## Installing SDK
+ In case depencies is requested
  ```
  sudo apt install -f
  ```
+ Version managers 
  + adding nodejs
    ```
    asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
    ```
  + java
    + adding java
    ```
    asdf plugin-add java https://github.com/halcyon/asdf-java.git
    ```
  + python
    + adding python
    ```
    asdf plugin-add python
    ```
  + php
    + adding php
    ```
    asdf plugin-add php https://github.com/asdf-community/asdf-php.git
    ```
+ SDKs installation
  + Install SDK's latest version:
    ```
    asdf install java latest:adoptopenjdk-8
    ```
  + Install SDK specific version:
    + List available version: 
      ```
      asdf list-all java
      ```
    + Install a candidate:
      ```
      asdf install java adoptopenjdk-11.0.16+8
      ```
+ Set SDK a Version
  + Global
    Global defaults are managed in $HOME/.tool-versions. Set a global version with:
    ```
    asdf global java latest
    ```
  + Local
    Local versions are defined in the $PWD/.tool-versions file (your current working directory). Usually, this will be the Git repository for a project. When in your desired directory execute:
    ```
    asdf local java adoptopenjdk-11.0.16+8
    ```

### REFERENCES
- [wsl](https://learn.microsoft.com/pt-br/windows/wsl/install)
- [Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)
- [Oh my ZSH](https://github.com/ohmyzsh/ohmyzsh)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [zsh-fast-syntax-highlighting](https://github.com/zdharma/fast-syntax-highlighting)
- [zsh-autocomplete](https://github.com/marlonrichert/zsh-autocomplete)
- [asdf - guide](https://asdf-vm.com/guide/getting-started.html)
- [asdf - plugins](https://github.com/asdf-vm/asdf-plugins)
- [eza](https://github.com/z-shell/zsh-eza)
- [bat](https://github.com/sharkdp/bat?ref=catalins.tech)
- [micro](https://github.com/zyedidia/micro#installation)

## Git & GitHub

1. Open terminal
2. Set Git UserName
```
git config --global user.name "you name"
```
4. Set Git UserEmail
```
git config --global user.email "you github email"
```
6. Generate New SSH
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
7. Add the SSH key to ssh-agent:
```
ssh-add ~/.ssh/id_ed25519
```
8. Open Generated SSH Key
```
cat ~/.ssh/id_ed25519.pub
```
Select and copy the content, `ctrl+shift+c`.

9. Add SSH Key to Github
   + Loogin / Siggin Github
   + Account Settings
   + SSH & GPG keys
   + New SSh Key
   + Title: Name it
   + Type: Authenticatio
   + Contente: Paste you SSH Key

10. Test Conection:
```
ssh -T git@github.com
```
+ Comparer the fingertip against: `SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU`. if equal, type yes.
+ Response should be `Hi, UserName...`

11. Ensuring ssh-agent is running
    + Open zsh/bash config
      ```
      sudo micro ~/.zshrc  
      ```
    + Add to the end
      ```
      eval $(ssh-agent -s)
      ```
    + Source it
      ```
      source ~/.zshrc
      ```
### REFERENCES
+ [Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git)
+ [Set user name](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git)
+ [Set User email](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)
+ [Generating & Adding new SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
+ [Test SSH Connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)
