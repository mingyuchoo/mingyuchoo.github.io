# Pacman Commands

## Completely remove

```bash
sudo pacman -Rns <package-name>
```

## Remove orphan packages

```bash
sudo pacman -Qdtq
# sudo pacman -Rs $(pacman -Qqtd)
```


## Install
```bash
sudo pacman -S <package-name>
```

## update the pacman package repository
```bash
sudo pacman -Sy

# or 


sudo pacman-mirrors -f 5 && sudo pacman -Syyu

```

## Install from AUR repository

* visit https://aur.archlinux.org/ 
* search package
* git clone ...

```bash
git clone https://...
// example: git clone https://AUR.archlinux.org/visual-studio-code-bin.git

cd <repository-directory>/

makepkg -s

sudo pacman -U <package-name>.pkg.tar.xz
```

