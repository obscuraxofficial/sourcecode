
Debian
====================
This directory contains files used to package obscuraxd/obscurax-qt
for Debian-based Linux systems. If you compile obscuraxd/obscurax-qt yourself, there are some useful files here.

## obscurax: URI support ##


obscurax-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install obscurax-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your obscurax-qt binary to `/usr/bin`
and the `../../share/pixmaps/obscurax128.png` to `/usr/share/pixmaps`

obscurax-qt.protocol (KDE)

