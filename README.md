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
ssh-keygen -t ed25519 -C "sifat@workstation" -f ~/.ssh/qp_ed25519
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
## Some update
```sh
sudo echo "/dev/nvme0n1p3 /mnt/Base auto defaults,nofail 0 0
//192.168.0.103/groot /mnt/Groot cifs username=mahi,password=$password,nofail 0 0
//192.168.0.103/mahi160 /mnt/Mahi160 cifs username=mahi,password=$password,nofail 0 0" >>/etc/fstab
sudo echo "Color" >>/etc/pacman.conf
```
## Themeing
### Themes and icons
```sh
yay --no-confirm adw-gtk3 tela-icon-theme
```
### Dynamic wallpaper from [https://github.com/manishprivet/dynamic-gnome-wallpapers](Dynamic Gnome Wallpapers)
```sh
curl -s https://wallpapers.manishk.dev/install.sh | bash -s Lakeside
```
## Installing app
## CLIs
```sh
curl -fsSL https://fnm.vercel.app/install | bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
### Non flatpak
```sh
yay --no-confirm brave-bin libre-office-fresh firefox-developer-edition visual-studio-code-bin docker docker-compose tlp flameshot neofetch htop exa duf onefetch ttf-jetbrains-mono-nerd timeshift timeshift-autosnap gparted 
```