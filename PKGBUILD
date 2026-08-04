# Maintainer: Aditya Shakya <adi1090x@gmail.com>

pkgname=archcraft-sway-free
pkgver=1.0
pkgrel=1
pkgdesc="Sway Configurations for Archcraft"
arch=('any')
url="https://github.com/archcraft-os/archcraft-sway"
license=('GPL3')
depends=('sway' 'swaybg' 'swayidle' 'swaylock' 'xorg-xwayland'
		'mako' 'waybar' 'rofi' 'foot' 'hyprpicker' 'hyprlock'
		'grim' 'slurp' 'imagemagick' 'wl-clipboard' 'wf-recorder'
		'mpv' 'pulsemixer' 'light' 'pastel' 'python-pywal' 'playerctl'
		'xdg-desktop-portal' 'xdg-desktop-portal-wlr' 'xdg-desktop-portal-gtk'
)
optdepends=('alacritty: default terminal emulator'
			'kitty: secondary terminal emulator'
			'thunar: default file manager'
			'geany: default text editor'
			'firefox: default web browser'
			'viewnior: default image viewer'
			'networkmanager-dmenu-git: control NetworkManager via rofi'
			'mpd: server-side application for playing music, used in statusbars and scripts'
			'mpc: minimalist command line interface to MPD'
			'xfce-polkit: a simple PolicyKit authentication agent'
			'yad: display graphical dialogs from shell scripts'
)
conflicts=('archcraft-sway' 'archcraft-swayfx')
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
	cp -af ../files/. "$srcdir"
}

package() {
	local _wcdir="$pkgdir"/etc/skel/.config/sway
	mkdir -p "$_wcdir"

	# Copy config files
	cp -r "$srcdir"/alacritty 		"$_wcdir"
	cp -r "$srcdir"/foot 			"$_wcdir"
	cp -r "$srcdir"/kitty 			"$_wcdir"
	cp -r "$srcdir"/mako 			"$_wcdir"
	cp -r "$srcdir"/rofi 			"$_wcdir"
	cp -r "$srcdir"/scripts 		"$_wcdir"
	cp -r "$srcdir"/theme 			"$_wcdir"
	cp -r "$srcdir"/wallpapers 		"$_wcdir"
	cp -r "$srcdir"/waybar 			"$_wcdir"

	chmod +x "$_wcdir"/scripts/*
	chmod +x "$_wcdir"/theme/theme.sh
	chmod +x "$_wcdir"/waybar/{spotify,lightmode}

	install -Dm 644 config   		"$_wcdir"/config
	install -Dm 644 sway-idle   	"$_wcdir"/sway-idle
	install -Dm 644 sway-input   	"$_wcdir"/sway-input
	install -Dm 644 sway-modes   	"$_wcdir"/sway-modes
	install -Dm 644 sway-output   	"$_wcdir"/sway-output
	install -Dm 644 sway-theme   	"$_wcdir"/sway-theme
	install -Dm 644 hyprlock.conf   "$_wcdir"/hyprlock.conf

	install -Dm 755 run-sway   					"$pkgdir"/usr/bin/run-sway
	install -Dm 644 archcraft-hook-sway.hook   	"$pkgdir"/usr/share/libalpm/hooks/archcraft-hook-sway.hook
}
