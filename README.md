# Web development environment on Ubuntu / Debian

## Essentials
```
sudo apt install -y -f build-essential curl wget git gdebi fuse3 gpg micro zsh bat fzf gnome-tweaks
```
+ Install EZA
  ```
  sudo mkdir -p /etc/apt/keyrings
  wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
  echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
  sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
  sudo apt update
  sudo apt install -y eza
  ```
+ Fix Bat
  ```
  mkdir -p ~/.local/bin
  ln -s /usr/bin/batcat ~/.local/bin/bat
  ```
+ theFuck
  ```
  sudo apt install -y -f python3 python3-pip python3-dev python3-setuptools
  pip3 install thefuck --user
  ```
+ LazyGit
  ```
  LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
  curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
  tar xf lazygit.tar.gz lazygit
  sudo install lazygit /usr/local/bin
  ```

### Turn ZSH the default bash
1. Type or paste on the console: 
```
chsh -s $(which zsh)
```
2. Close The terminal and open again 
3. Choose ZSH Setting (2. Populate with...)
4. Install Oh-My-Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
5. Install Zsh Plugins

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
  
+ asdf
  ```
  git clone https://github.com/asdf-vm/asdf.git ~/.asdf
  ```
  or
  ```
  git clone https://github.com/asdf-vm/asdf.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/asdf
  ```

+ zsh-interactive-cd
  ```
  git clone https://github.com/mrjohannchang/zsh-interactive-cd.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-interactive-cd
  ```

6. Enable Plugins  
```
sudo nano ~/.zshrc  
```
+ Press `F6` then type `plugins`
  ```
  plugins=(git zsh-eza extract colored-man-pages ubuntu command-not-found thefuck fzf asdf pip pipenv gradle spring gulp grunt npm yarn ng dotenv composer laravel docker docker-compose zsh-syntax-highlighting zsh-autosuggestions fast-syntax-highlighting zsh-autocomplete)
  ```  
+ Set up zsh-interactive-cd
  ```
  # Set up zsh-interactive-cd
  source  /home/osmar/.oh-my-zsh/custom/plugins/zsh-interactive-cd/zsh-interactive-cd.plugin.zsh
  ```
  
+ Press `F6` then type `themes`
  ```
  ZSH_THEME="af-magic"
  ```
+ Source it
```
source ~/.zshrc
```

### Nerd Fonts
+ Download a Font.zip
+ Donwload Patcher.zip
+ Add Dependecy
```
sudo apt install fontforge python3 python3-fontforge python3-argcomplete python-is-python3
pip install argparse
```
* Extract the patcher.zip
* Extact the Font.zip
* Move the Font folder to Patcher folder
* Make a Python install.py inside patcher folder:
  ```
  import os
  import subprocess
  # Change the Dir name to your font's folder name
  fontsDir = "JetBrainsMono"
  # Change the parameters bellow as needed
  command = "./font-patcher {}" 
  fontFiles = [f for f in os.listdir(fontsDir) if os.path.isfile(os.path.join(fontsDir, f))]
  for font in fontFiles:
      fontPath = os.path.join(fontsDir, font)
      subprocess.run(command.format(fontPath), shell=True)
  ```

### REFERENCES
- [Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)
- [Oh my ZSH](https://github.com/ohmyzsh/ohmyzsh)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [zsh-fast-syntax-highlighting](https://github.com/zdharma/fast-syntax-highlighting)
- [zsh-autocomplete](https://github.com/marlonrichert/zsh-autocomplete)

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

## Node

1. Open terminal
2. Download and import the Nodesource GPG key
```
sudo apt update && sudo apt-get install -y ca-certificates curl gnupg
```
```
sudo mkdir -p /etc/apt/keyrings
```
```
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```

3. Create deb repository
```
NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
```

> Optional: NODE_MAJOR can be changed depending on the version you need.
>
> NODE_MAJOR=16
>
> NODE_MAJOR=18
>
> NODE_MAJOR=20

4. Run Update and Install
```
sudo apt update && sudo apt install nodejs -y
```

### REFERENCES
[Node Installation](https://github.com/nodesource/distributions)

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
