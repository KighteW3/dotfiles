# .DOTFILES

This is my personal repo for my .dotfiles configuration, you can fork it or just copy, feel free to be inspirated by it.

## Dependencies

There are some dependencies that are a "must to" to have my exact configuration, misc and personal ones are just optional and can be replaced.

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
    - xterm
- sddm
    - (systemctl enable sddm.service)
- stow
- blueman-manager
    - bluetooth
    - bluez
- tlp
- acpi
    - acpid
- brightnessctl

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
    - linux-lts
- amd-ucode (or intel-ucode)
- sof-firmware
- linux-firmware-marvell
- dhcp
    - dhcpd (systemctl enable dhcpd.service)
- networkmanager
    - (systemctl enable NetworkManager.service)
- neovim, vim, vi
- man-db, man-pages, texinfo
- grub (and efigrubmgr if uefi)
    - dosfstools
    - mtools
    - (installation: grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck)
    - (configuration: grub-mkconfig -o /boot/grub/grub.cfg)
- os-prober

### My personal preferences

- tmux
- neovim (latest)
    - py-nvim
- python3
    - pip3
- nodejs
    - npm
- paru
- rustup
- docker
    - docker-compose
- keycommands
    - localectl set-x11-keymap (your layout)
    - exec setxkbmap -layout no


## Installation

>cd $HOME

>git clone https://github.com/KighteW3/dotfiles.git

>cd dotfiles

>stow .
