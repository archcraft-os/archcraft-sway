<h1 align="center">SWAY</h1>

[![Sway Main Video](screenshots/sway_4.png)](https://youtu.be/ASlQcf8Jc0I)

<p align="center">The ultimate Sway configuration (A Desktop Environment Like Experience)</p>

---

## Overview

Sway is a tiling Wayland compositor and a drop-in replacement for the i3 window manager for X11. It works with your existing i3 configuration and supports most of i3's features, plus a few extras. 

- **Operating System** : `Archcraft`
- **Window Manager** : `Sway`
- **Status Bar** : `Waybar`
- **Launcher** : `Rofi` / `Wofi`
- **Session Manager** : `Rofi` / `Wlogout`
- **Notifications** : `Mako`
- **Terminal** : `Foot`
- **File Manager** : `Thunar`
- **Text Editor** : `Geany`
- **Web Browser** : `Firefox`

## Installation
- Get the files from : [Ko-fi :coffee:](https://ko-fi.com/s/10f2e87af3) <sup>[**`Why Paid`**](https://github.com/adi1090x/adi1090x/blob/master/WHY.md)</sup>
- Extract The file **sway.tar.gz** with : `tar -xzvf sway.tar.gz`
- If you are using **`Archcraft`** (`Required: 2023 or later`) as your OS, You can just install the provided package with : `sudo pacman -U archcraft-sway-3.0-3-any.pkg.tar.zst`
- If you want to install this setup on _Arch Linux_ or on any _other distro_, follow the points below :
  - Install the following programs on your computer: `sway` `swaybg` `swayidle` `swaylock` `wlroots` `wl-clipboard` `waybar` `wofi`  `kanshi` `foot` `mako` `grim` `slurp` `wf-recorder` `light` `yad` `wlogout` `thunar` `geany` `mpv` `mpd` `mpc` `viewnior` `imagemagick` `xfce-polkit` `xorg-xwayland` `xdg-desktop-portal-wlr` `playerctl`
  - After installing programs above, Create sway directory in **`~/.config`** : `mkdir -p ~/.config/sway`
  - Copy Everything from _dotfiles_ to **`~/.config/sway`** : `cp -r ./dotfiles/* ~/.config/sway/` 
  - Logout and login to your amazingly configured Sway WM.

### Appearance

Install the following `theme`, `icon pack`, `cursors` and `fonts` for overall appearance.

- GTK Theme : [Manhattan gtk theme](https://github.com/archcraft-os/archcraft-themes/tree/main/archcraft-gtk-theme-manhattan)
- Icon Theme : [Luv-Folders-Dark icon theme](https://github.com/archcraft-os/archcraft-icons/tree/main/archcraft-icons-luv/files)
- Cursor Theme : [Qogir cursor theme](https://www.gnome-look.org/p/1366182/)
- Fonts : [JetBrainsMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/JetBrainsMono.zip), [Iosevka Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Iosevka.zip), [Icomoon Feather](https://github.com/archcraft-os/archcraft-packages/blob/main/archcraft-fonts/files/icon-fonts/Icomoon-Feather.ttf), [Archcraft](https://github.com/archcraft-os/archcraft-packages/blob/main/archcraft-fonts/files/icon-fonts/archcraft.ttf)

## Config Structure
```
~/.config
└── sway              : Sway config directory
    ├── foot          : Terminal config
    ├── mako          : Notification daemon config
    │   └── icons     : Notification icons
    ├── rofi          : Rofi config files
    ├── scripts       : Various scripts for functionality
    ├── wallpapers    : Wallpapers
    ├── waybar        : Statusbar config
    ├── wlogout       : Wlogout config
    │   └── icons     : Session icons
    ├── wofi          : Launcher config
    ├── config        : Main sway config
    ├── sway-idle     : Sway idle config
    ├── sway-input    : Sway input config
    ├── sway-modes    : Sway mode config
    ├── sway-output   : Sway output config
    └── sway-theme    : Sway theme config
```

> By default, **`wofi`** is used as app launcher.
>
> But, If you want to use **rofi** instead of **wofi**, First make sure you install the [wayland fork of rofi](https://github.com/lbonn/rofi). Edit the config file `~/.config/sway/config` and uncomment rofi keybindings (and, comment the wofi stuff as well).

> By default, **`MPD`** is used on waybar for music.
>
> But, If you want to use **Spotify** instead of **MPD**, Edit the config file `~/.config/sway/waybar/config` and uncomment the spotify module (and, comment the MPD module as well).

## Nvidia
If you're on `Archcraft` and install the provided package, There's nothing else you need to do in order to run it on Nvidia machine. The package's post_installation script does it all, And the compositor should work fine.

If you're running any other distribution and want to install this setup on your Nvidia machine, You need to do some tweaking. In this guide, I'm assuing you're using **Arch Linux**. Follow the steps below to make this wayland compositor work on Nvidia :

- Install **Nvidia Drivers** on your system. [NVIDIA](https://wiki.archlinux.org/title/NVIDIA) 
- Edit `/etc/mkinitcpio.conf` file and add **`nvidia`** kernel modules
```
MODULES="nvidia nvidia_modeset nvidia_uvm nvidia_drm"
```

- In the same file, Remove `kms` hook from hooks array if present.
- Rebuild your initrd file with : `sudo mkinitcpio -P linux`
- Edit `/etc/default/grub` file and add **`nvidia_drm.modeset=1`** kernel parameter for Nvidia
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia_drm.modeset=1 ..."
```

- Update your grub config file with : `sudo grub-mkconfig -o /boot/grub/grub.cfg`
- Reboot your Nvidia Machine and login to your wayland compositor, It should work now.

More Information: [NVIDIA#Installation](https://wiki.archlinux.org/title/NVIDIA#Installation), [NVIDIA#DRM_kernel_mode_setting](https://wiki.archlinux.org/title/NVIDIA#DRM_kernel_mode_setting)

## Keybindings

| Keys | Action |
| --- | --- |
| <kbd>super + Return</kbd> | Open terminal |
| <kbd>super + shift + Return</kbd> | Open floating terminal |
| <kbd>super + alt + Return</kbd> | Open terminal with custom geometry |
| <kbd>super + T</kbd> | Open fullscreen terminal |
| <kbd>super + shift + F</kbd> | Open file manager |
| <kbd>super + shift + E</kbd> | Open text editor |
| <kbd>super + shift + W</kbd> | Open web browser|
| <kbd>super + D</kbd> | Run app launcher |
| <kbd>super + N</kbd> | Open network manager |
| <kbd>super + X</kbd> | Run session manager |
| <kbd>super + P</kbd> | Run colorpicker |
| <kbd>super + C/Q</kbd> | Kill active window |
| <kbd>ctrl + alt + L</kbd> | Run lockscreen |
| <kbd>super + shift + C</kbd> | Reload sway config |
| <kbd>super + shift + Q</kbd> | Quit sway session |
| <kbd>super + 1,2..9,0</kbd> | Change workspace from 1 to 10 |
| <kbd>super + shift + 1,2..9,0</kbd> | Move active window to repective workspace |
| <kbd>super + Left</kbd> | Change focus to the left container |
| <kbd>super + Right</kbd> | Change focus to the right container |
| <kbd>super + Up</kbd> | Change focus to the upper container |
| <kbd>super + Down</kbd> | Change focus to the lower container |
| <kbd>super + shift + Left</kbd> | Move focused container to the left |
| <kbd>super + shift + Right</kbd> | Move focused container to the right |
| <kbd>super + shift + Up</kbd> | Move focused container to the upper |
| <kbd>super + shift + Down</kbd> | Move focused container to the lower |
| <kbd>super + B</kbd> | Split container horizontally |
| <kbd>super + V</kbd> | Split container vertically |
| <kbd>super + S</kbd> | Change container layout to stacked |
| <kbd>super + W</kbd> | Change container layout to tabbed |
| <kbd>super + E</kbd> | Change container layout to toggle split |
| <kbd>super + F</kbd> | Toggle fullscreen mode |
| <kbd>super + Space</kbd> | Toggle floating mode |
| <kbd>super + shift + Space</kbd> | Toggle focus b/w tile and floating mode |
| <kbd>super + R</kbd> | Start resizing mode |
| <kbd>super + M</kbd> | Start moving mode |
| <kbd>super + G</kbd> | Start gaps mode |
| <kbd>super + O</kbd> | Start opacity mode |
| <kbd>super + A</kbd> | Focus parent container |
| <kbd>super + Z</kbd> | Focus child container |
| <kbd>super + Minus</kbd> | Toggle scratchpad window |
| <kbd>super + shift + Minus</kbd> | Move the currently focused window to the scratchpad |

## Screenshots

| Screenshot 1 | Screenshot 2 |
| --- | --- |
|![sway](screenshots/sway_1.png)|![sway](screenshots/sway_2.png)|

| Screenshot 3 | Screenshot 4 |
| --- | --- |
|![sway](screenshots/sway_3.png)|![sway](screenshots/sway_4.png)|

---

### See Also

| [**`archcraft-river`**](https://github.com/archcraft-os/archcraft-river) | [**`archcraft-wayfire`**](https://github.com/archcraft-os/archcraft-wayfire) | [**`archcraft-hyprland`**](https://github.com/archcraft-os/archcraft-hyprland) | [**`archcraft-newm`**](https://github.com/archcraft-os/archcraft-newm) |
| --- | --- | --- | --- |
|[![River](https://raw.githubusercontent.com/archcraft-os/archcraft-river/main/screenshots/River_4.png)](https://github.com/archcraft-os/archcraft-river)|[![Wayfire](https://raw.githubusercontent.com/archcraft-os/archcraft-wayfire/main/screenshot.png)](https://github.com/archcraft-os/archcraft-wayfire)|[![Hyprland](https://raw.githubusercontent.com/archcraft-os/archcraft-hyprland/main/screenshots/dark/hypr_dark_2.png)](https://github.com/archcraft-os/archcraft-hyprland)|[![Newm](https://raw.githubusercontent.com/archcraft-os/archcraft-newm/main/screenshots/solid/newm_5.png)](https://github.com/archcraft-os/archcraft-newm)|
