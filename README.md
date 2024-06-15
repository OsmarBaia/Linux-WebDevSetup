# WLS for Development
## Installing WSL
+ Open powershell as admin
  ```
  wsl – -install
  ```
+ Reboot
  ```
  Restart-Computer
  ```
  
## WSL Essentials
+ Open wsl and access root
  ```
  cd /
  ```
+ Update & Upgrade
  ```
  sudo apt update && sudo apt upgade && sudo apt install -f
  ```
+ Install main dependencies
  ```
  sudo apt install -f git curl wget build-essential
  ```

## Zsh & Oh-My-Zsh
+ zsh
  ```
  sudo apt install -f zsh
  chsh -s $(which zsh)
  ```

+ Oh-My-Zsh
  ```
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
  ```

## asdf - SDK version manager
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.0
```

## Terminal upgrades
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
+ Shearch for `ZSH_THEME`
  ```
  ZSH_THEME="af-magic"
  ```  
+ Shearch for `plugins`
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
+ Adding version managers
  + add nodejs version manager
    ```
    asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
    ```
  + java
    + add java version manager
    ```
    asdf plugin-add java https://github.com/halcyon/asdf-java.git
    ```
  + python
    + add python version manager
    ```
    asdf plugin-add python
    ```
  + php
    + add php version manager
    ```
    asdf plugin-add php https://github.com/asdf-community/asdf-php.git
    ```
+ Adding SDKs
  + Install SDK latest version:
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
- [asdf - plugins](https://github.com/asdf-community)
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

### REFERENCES
+ [Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git)
+ [Set user name](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git)
+ [Set User email](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)
+ [Generating & Adding new SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
+ [Test SSH Connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)


## Front End - React Stack
1. Prettier - Code Formatter
```
sudo npm install -g prettier 
```
2. SaSS - CSS Pre-processor
```
sudo npm install -g sass
```
3. TypeScript - Typecheck for JavaScript
```
sudo npm install -g typescript
```
4. Eslint - JavaScript Coding Conventions
```
sudo npm install -g prettier-eslint eslint eslint-config-prettier eslint-plugin-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-react eslint-plugin-react-hooks
```
5. Gulp - Autamate borig stuff
```
sudo npm install -g gulp-cli gulp-sass gulp-typescript gulp-eslint
```
6. Vite - Project Builder
```
sudo npm install -g vite @vitejs/plugin-react
```
7 Redux - React State Manager
```
sudo npm install -g react-redux
```
8. Cypress
```
sudo apt install libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libnss3 libxss1 libasound2 libxtst6 xauth xvfb
```
```
npm install -g cypress
```

### New Project
1. Create New project
+ Vite:
```
npm create vite@latest my-app --template vanilla
```
> supported template: vanilla, vanilla-ts, vue, vue-ts, react, react-ts, react-swc, react-swc-ts, preact, preact-ts, lit, lit-ts, svelte, svelte-ts, solid, solid-ts, qwik, qwik-ts

+ Redux-React-Vite-Ts Project:
```
npx degit reduxjs/redux-templates/packages/vite-template-redux my-app
```
2. Start npm:
```
npm init --y
```
3. Install basic dependecies:
```
npm install
```
4. Teste it:
```
npm start
```
5. Add Personal dependencies
```
npm install 
sass
bootstrap@5.3.2
typescript
eslint
prettier
prettier-eslint
eslint-config-prettier
eslint-plugin-prettier
@typescript-eslint/parser
@typescript-eslint/eslint-plugin
eslint-plugin-react
eslint-plugin-react-hooks
gulp
gulp-sass
gulp-typescript
gulp-eslint
cypress
--save-dev
```
6. Start Eslint
```
eslint --init
```
8. Config Files:
```
```

### REFERENCES
+ [Sass Installation](https://sass-lang.com/install/)
+ [TypeScript Installation](https://www.typescriptlang.org/download)
+ [gulp Installation](https://gulpjs.com/docs/en/getting-started/quick-start/)
+ [bootStrap Installation](https://getbootstrap.com/docs/5.0/getting-started/download/)
+ [Eslint & Prettier](https://dev.to/devland/set-up-a-nodejs-app-with-eslint-and-prettier-4i7p)
+ [Eslint & React](https://www.freecodecamp.org/news/how-to-add-eslint-to-your-react-project/)
+ [Eslint & React PT-BR](https://felipecesar.dev/posts/como-configurar-o-prettier-e-eslint-em-projetos-react/)
+ [Eslint & TypeScript](https://khalilstemmler.com/blogs/typescript/eslint-for-typescript/)
+ [Eslint & Gulp](https://gist.github.com/ConnectExtend/be068b68d54dcc27db9154761ec97fff)
+ [Redux-React & Vite](https://redux.js.org/introduction/getting-started)
+ [Cypress](https://docs.cypress.io/guides/getting-started/installing-cypress)
