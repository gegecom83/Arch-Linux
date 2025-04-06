# Arch Linux

[WIKI officiel de Arch Linux](https://wiki.archlinux.org/title/Arch_Linux_(Fran%C3%A7ais))


## Installation

Téléchargez et lancez la dernière iso de Arch Linux : https://archlinux.org/download/


#### 1. Configurer le clavier en français

```sh
loadkeys fr
```

#### 2. Configurer votre Wi-Fi

```sh
iwctl
```
    
Puis (remplacez VOTRE-NOM-WIFI par le nom de votre wifi)

```sh
station wlan0 connect VOTRE-NOM-WIFI (SSID)
```

Entrez votre mot de passe wifi puis tapez `quit` pour quitter iwctl.

#### 3. Utilisation d'archinstall

Vous pouvez simplement taper : ```archinstall``` pour le lancer.

**Mise à jour de archinstall :**

```sh
pacman -Sy archinstall
```

<br>

## Post-installation

#### 2. **Installation d'un AUR helper**

[Yay](https://github.com/Jguer/yay)
   
```sh
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```

Ajout du support pour les mises à jour des paquets git. (Normalement, cela ne doit être fait qu'une seule fois)

```sh
yay -Y --gendb
yay -Y --devel --save
```

--- 

<br>

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

Tous les cas ne sont pas gérés par les points précédents, des fois les drivers sont sur AUR il faut fouiller comme par exemple pour la [brother-mfc-9340cdw](https://aur.archlinux.org/packages/brother-mfc-9340cdw).

--- 

<br>

#### Bluetooth <a name="bluetooth"></a>

La seconde commande ci-dessous demande à systemd de démarrer immédiatement le service bluetooth, et aussi de l'activer à chaque démarrage.

```sh
yay -S --needed bluez bluez-utils bluez-plugins
sudo systemctl enable --now  bluetooth.service
```

--- 

<br>

### LOGICIEL DE BASE <a name="logiciel-de-base"></a>

--- 

<br>

#### Logiciels GNOME

Voici divers logiciels pour graphisme, vidéo (édition, support de codec), utilitaires d'interface graphique, etc.

```sh
sudo pacman -S --needed xdg-desktop-portal-kde okular print-manager kdenlive gwenview spectacle partitionmanager ffmpegthumbs qt6-wayland kdeplasma-addons powerdevil kcalc plasma-systemmonitor qt6-multimedia qt6-multimedia-gstreamer qt6-multimedia-ffmpeg kwalletmanager
```

--- 

<br>

#### Arch Update <a name="arch-update"></a>

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
