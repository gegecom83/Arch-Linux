# Arch Linux

[ArchWiki](https://wiki.archlinux.org/title/Main_page)

## Installation guide

Download arch's iso : https://archlinux.org/download/

#### 1. Keyboard layout

```sh
loadkeys fr
```

#### 2. Connect to the wireless

```sh
iwctl
```

List all Wi-Fi devices:
```sh
device list
```

Initiate a scan for networks:
```sh
station wlan0 scan
```

List all available networks:
```sh
station wlan0 get-networks
```

Connect to a network:
```sh
station wlan0 connect "your_network_name"
```

Enter your "your_network_name" password:
```sh
your_network_name password
```

To leave iwctl:
```sh
exit
```

#### 3. archinstall

Installation:
```sh
sudo pacman -S archinstall
```

Running the guided installer:
```sh
archinstall
```

<br>

## Post-installation

#### 1. Package manager

[pacman](https://wiki.archlinux.org/title/Pacman)

To update all packages on the system:
```sh
sudo pacman -Syu
```

To install a single package or list of packages, including dependencies, issue the following command:
```sh
sudo pacman -S package_name1 package_name2 ...
```

To remove a package with configuration and its dependencies which are not required by any other installed package:
```sh
sudo pacman -Rns package_name
```

To search for packages in the database, searching both in packages' names and descriptions:
```sh
sudo pacman -Ss string1 string2 ...
```

To search for already installed packages:
```sh
sudo pacman -Qs string1 string2 ...
```

To search for package file names in remote packages:
```sh
sudo pacman -F string1 string2 ...
```

To display extensive information about a given package:
```sh
sudo pacman -Si package_name
```

To display extensive information locally installed packages:
```sh
sudo pacman -Qi package_name
```

To list of the files installed package:
```sh
sudo pacman -Q
```

To install a 'local' package that is not from a remote repository:
```sh
sudo pacman -U /path/to/package/package_name-version.pkg.tar.zst
```

To list orphaned packages:
```sh
sudo pacman -Qdt
```

To remove all the cached packages that are not currently installed, and the unused sync databases:
```sh
sudo pacman -Sc
```

#### 2. AUR helper

[yay](https://github.com/Jguer/yay)
 
 Source:
   
```sh
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

First Use:

```sh
yay -Y --gendb
```
```sh
yay -Y --devel --save
```

#### 3. Printers

Install the necessary printing system, fonts, and network service discovery components:
```sh
sudo pacman -S ghostscript gsfonts cups cups-filters cups-pdf system-config-printer avahi
```

Enable and start printing and discovery services:
```sh
sudo systemctl enable --now avahi-daemon
```
```sh
sudo systemctl enable --now cups
```

Install universal printer drivers via the Foomatic and Gutenprint frameworks:
```sh
sudo pacman -S foomatic-db-engine foomatic-db foomatic-db-ppds foomatic-db-nonfree foomatic-db-nonfree-ppds gutenprint foomatic-db-gutenprint-ppds
```

HP Linux Imaging and Printing (HPLIP) with GUI dependencies:
```sh
sudo pacman python-pyqt5 hplip
```

Epson ESC/P-R drivers from the AUR:
```sh
yay epson-inkjet-printer-escpr epson-inkjet-printer-escpr2 epson-inkjet-printer-201601w epson-inkjet-printer-n10-nx127
```

#### 4. Bluetooth

Bluetooth support:
```sh
sudo pacman -S bluez bluez-utils bluez-plugins bluez-hid2hci bluez-libs
```
```sh
sudo systemctl enable --now  bluetooth.service
```

<br>

## Desktop Environment

Installs a curated selection of useful packages.

#### 1. GNOME

```sh
sudo pacman -S firefox gimp libreoffice-fresh evolution file-roller dconf-editor gnome-themes-extra gnome-browser-connector gst-plugin-pipewire adw-gtk-theme gst-plugins-base gst-plugins-bad gst-plugins-good gst-plugins-ugly gst-libav qt5ct
```
```sh
yay adwaita-qt5 adwaita-qt6 qadwaitadecorations-qt5 qadwaitadecorations-qt6
```

qt5ct
```sh
nano ~/.profile
```
```sh
export QT_QPA_PLATFORMTHEME="qt5ct"
```
```sh
nano ~/.bash_profile
```
```sh
[[ -f ~/.profile ]] && . ~/.profile
```

#### 2. KDE

```sh
sudo pacman -S firefox krita kmail libreoffice-fresh gst-plugin-pipewire gst-plugins-base gst-plugins-bad gst-plugins-good gst-plugins-ugly gst-libav sddm-kcm qt5-declarative breeze-gtk kde-gtk-config 
```

#### 3. Arch Update

[arch-update](https://github.com/Antiz96/arch-update)

An update notifier & applier for Arch Linux that assists you with important pre / post update tasks.
Includes a dynamic & clickeable systray applet for an easy integration with any Desktop Environment / Window Manager.

```sh
yay arch-update
```
```sh
systemctl --user enable --now arch-update.timer
```
```sh
systemctl --user enable --now arch-update-tray.service
```

Style to be used for the systray applet icon. Valid values are the available style / color variants for the icon set
"light" "dark" "blue".

```sh
arch-update --gen-config
```
```sh
nano ~/.config/arch-update/arch-update.conf
```
```sh
TrayIconStyle=light
```
--- 

<br>
