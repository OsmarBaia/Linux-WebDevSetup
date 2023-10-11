# Web development environment on Ubuntu / PopOS

## Essentials
```
sudo apt install build-essential curl wget git 
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
   + Type: Authentication
   + Contente: Paste you SSH Key

10. Test Conection:
```
ssh -T git@github.com
```
+ Comparer the fingertip against: `SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU`. if equal, type yes.
+ Response should be `Hi, UserName`

### REFERENCES
[Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git)
[Set user name](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git)
[Set User email](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)
[Generating & Adding new SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[Test SSH Connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)
