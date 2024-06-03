# .DOTFILES

This is my personal repo for my .dotfiles configuration, you can fork it or just copy, feel free to be inspirated by it.

## Dependencies

There are some dependencies that are a "must to" to have my exact configuration, misc ones are just optional and can be replaced.

### Tools

- i3
    - i3-wm
    - i3blocks
    - i3lock
    - i3status
- gtk
    - gtk2
    - gtk3
    - gtk4
- xorg (all, including xorg-xinit)
- tmux
- neovim (latest)
    - py-nvim
- python3
    - pip3
- nodejs
    - npm

### Misc

- polybar
    - Robot Mono fonts
- alacritty
    - 0xProto Nerd Font
- picom
- feh
- rofi

### System

- Scratch
    - base
    - base-devel
    - linux
    - linux-headers
    - linux-firmware
- amd-ucode
- sof-firmware
- linux-firmware-marvell
- networkmanager
- neovim, vim, vi
- man-db, man-pages, texinfo
- grub, grubootmgr

## Installation

> cd $HOME
git clone https://github.com/KighteW3/dotfiles.git\n
cd dotfiles
stow --adopt .
