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
## Setup SSH
### Generate ssh key
```sh
ssh-keygen -t ed25519 -C "sifat@workstation" -f ~/.ssh/qa_ed25519
ssh-keygen -t ed25519 -C "mahi@workstation" -f ~/.ssh/id_ed25519
```
### Create config
```sh
touch ~/.ssh/config
echo "
# Primary GitHub account
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

# Secondary GitHub account
Host qp.github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/qp_ed25519
" >>~/.ssh/config
```
