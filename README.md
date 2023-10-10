# Web development enviormento on Ubuntu / PopOS

## Essentials
```
sudo apt install build-essential curl wget git 
```

## Zsh & Oh My Zsh
+ Instal ZSH
```
sudo apt install zsh
```
+ Turn it default bash
```
sudo chsh -s $(which zsh)
```
+ Install Oh My Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
+ Install Plugins
```
 sudo apt install zsh-syntax-highlighting zsh-autosuggestions fzf thefuck 
```
- zsh-fast-syntax-highlighting plugin 
```
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```
- zsh-autocomplete plugin
```
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
```
+ Enable Plugins  
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

# References
- [Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)
- [Oh my ZSH](https://github.com/ohmyzsh/ohmyzsh)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [zsh-fast-syntax-highlighting](https://github.com/zdharma/fast-syntax-highlighting)
- [zsh-autocomplete](https://github.com/marlonrichert/zsh-autocomplete)
