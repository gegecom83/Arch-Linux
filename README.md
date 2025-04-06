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
station wlan0 connect "your_name_network"
```

Enter your "your_name_network" password:

```sh
your_name_network password
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
yay -Y --devel --save
```

#### 3. Imprimantes

1. **Essentiels** :
   - Installez les paquets nécessaires pour la gestion des imprimantes :
     ```sh
     sudo pacman -S --needed ghostscript gsfonts cups cups-filters cups-pdf system-config-printer avahi
     ```
   - Activez et démarrez les services Avahi et CUPS :
     ```sh
     sudo systemctl enable --now avahi-daemon cups
     ```
   - Désactivez le service systemd-resolved (si vous ne l'utilisez pas) :
     ```sh
     sudo systemctl disable systemd-resolved
     ```

2. **Pilotes** :
   - Installez les paquets pour les pilotes d'imprimantes génériques (Ces pilotes gèrent la plus part des imprimantes) :
     ```sh
     sudo pacman -S --needed foomatic-db-engine foomatic-db foomatic-db-ppds foomatic-db-nonfree foomatic-db-nonfree-ppds gutenprint foomatic-db-gutenprint-ppds
     ```

3. **Imprimantes HP** :
   - Pour les imprimantes HP, installez également les paquets suivants :
     ```sh
     yay -S --needed python-pyqt5 hplip
     ```

4. **Imprimantes Epson** :
   - Pour les imprimantes Epson, utilisez les commandes suivantes :
     ```sh
     yay -S --needed epson-inkjet-printer-escpr epson-inkjet-printer-escpr2 epson-inkjet-printer-201601w epson-inkjet-printer-n10-nx127
     ```

#### 4. Bluetooth

La seconde commande ci-dessous demande à systemd de démarrer immédiatement le service bluetooth, et aussi de l'activer à chaque démarrage.

```sh
yay -S --needed bluez bluez-utils bluez-plugins
sudo systemctl enable --now  bluetooth.service
```

<br>

## LOGICIEL DE BASE

#### 1. Logiciels GNOME

Voici divers logiciels pour graphisme, vidéo (édition, support de codec), utilitaires d'interface graphique, etc.

```sh
sudo pacman -S --needed xdg-desktop-portal-kde okular print-manager kdenlive gwenview spectacle partitionmanager ffmpegthumbs qt6-wayland kdeplasma-addons powerdevil kcalc plasma-systemmonitor qt6-multimedia qt6-multimedia-gstreamer qt6-multimedia-ffmpeg kwalletmanager
```

#### 1. Arch Update

[Arch-Update  : Notifie les updates de Arch et aide aux tâches importantes avant et après l'update.](https://youtu.be/QkOkX70SEmo?si=EwB-rSTV5dMNbv5D)

- [arch-update](https://github.com/Antiz96/arch-update)

Arch Update est un notificateur/aplicateur de mise à jour pour Arch Linux qui vous assiste dans les tâches importantes avant et après la mise à jour et qui inclut une icône cliquable (.desktop) pouvant être facilement intégrée à n'importe quel environnement de bureau/gestionnaire de fenêtres, dock, barre de statut/lançage ou menu d'application.
Support optionnel pour les mises à jour des paquets AUR/Flatpak et les notifications de bureau.

```sh
yay -S arch-update
systemctl --user enable --now arch-update.timer
systemctl --user enable --now arch-update-tray.service
```

--- 

<br>
