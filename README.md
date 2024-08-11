# Setup arch linux

## Initial setup
### Install git, zsh
```sh
sudo pacman -S git zsh
```
### Install yay
```sh
sudo pacman -Sy --needed git base-devel
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

## Terminal setup
### Install oh my zsh
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
### Zsh plugins
```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```
### Starship prompt
```sh
curl -sS https://starship.rs/install.sh | sh
```
