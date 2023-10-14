# Web development environment on Ubuntu / PopOS

## Essentials
```
sudo apt install build-dep build-essential curl wget git 
```

## Zsh & Oh My Zsh
1. Instal ZSH
```
sudo apt install zsh
```
2. Turn it default bash
```
sudo chsh -s $(which zsh)
```
3. Install Oh My Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
4. Install Plugins
```
 sudo apt install zsh-syntax-highlighting zsh-autosuggestions fzf thefuck 
```   
+ zsh-fast-syntax-highlighting plugin
```
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```
+ zsh-autocomplete plugin
```
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
```
5. Enable Plugins  
```
sudo nano ~/.zshrc  
```
+ Press `F6` then type `plugins`
+ Erase the line and paste this one:
```
plugins=(
git 
zsh-autosuggestions 
zsh-syntax-highlighting 
fast-syntax-highlighting 
colored-man-pages 
command-not-found 
zsh-autocomplete
fzf 
thefuck 
ubuntu 
npm 
dotenv 
gulp 
grunt
composer 
laravel 
docker
docker-compose
)

```
+ Source it
```
sudo source ~/.zshrc
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
+ Response should be `Hi, UserName`

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
