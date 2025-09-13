# Dotfiles với Bare Repo

```bash
## Khởi tạo trên máy cũ
git init --bare $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
echo ".dotfiles" >> ~/.gitignore

## Thêm file / thư mục vào quản lý
config add ~/.zshrc
config add ~/.xprofile
config add ~/.config/hypr/hyprland.conf
config add ~/.config/hypr/config/user-config.conf
config add ~/.config/autostart

## Commit và push lên GitHub ( luu y dung config thay cho git )

config commit -m "Add dotfiles"
config branch -M main
config remote add origin git@github.com:USERNAME/dotfiles.git
config push -u origin main

## Khôi phục trên máy mới

git clone --bare git@github.com:USERNAME/dotfiles.git $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config checkout

## xy ly loi neu da ton tai
mkdir -p .dotfiles-backup
config checkout 2>&1 | grep -E "\s+\." | awk '{print $1}' | \
  xargs -I{} mv {} .dotfiles-backup/{}
config checkout
```
# Arch btw
