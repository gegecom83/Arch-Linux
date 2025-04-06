# Install
loadkeys fr-latin1
iwctl
device list
station wlan0 scan
station wlan0 get-networks
station wlan0 connect SFR_9328
5uqf76gnqf6kem55nrhd
exit
archinstall

# wlan
nmcli device wifi connect SFR_9328 password 5uqf76gnqf6kem55nrhd

# Vmware
sudo pacman -S open-vm-tools
sudo systemctl enable/start vmtoolsd.service
sudo systemctl enable/start vmware-vmblock-fuse.service
sudo pacman -S gtkmm3

# Bookmarks
https://archlinux.org
https://archlinux.fr
https://www.gnome.org
https://kde.org
https://www.xfce.org
https://www.linuxtricks.fr
https://www.gaminglinux.fr
https://codeberg.org/Gaming-Linux-FR
https://github.com/aaaaadrien
https://github.com/Antiz96
https://github.com/Cardiacman13

# Package manager
update="sudo pacman -Syy"
upgrade="sudo pacman -Syu"
fullupgrade="yay"
install="sudo pacman -S"
remove="sudo pacman -Rns"
pkglist="pacman -Q"
pkgaurlist="pacman -Qm"
pkginfo="pacman -Qi"
pkgsearch="pacman -Ss"
pkgfile="pacman -Qo"
pkgfilesearch="pacman -F"
pkgfilelist="pacman -Ql"
pkgfilelistsearch="pacman -Fl"
cleancache="sudo pacman -Sc"
cleanundepend="yay -Yc"
cleanorphans="sudo pacman -Qtdq | sudo pacman -Rns -"
cleanarch='yay -Sc && yay -Yc'

# AUR helper
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
yay -Y --gendb
yay -Y --devel --save

# Arch-update
yay arch-update
systemctl --user enable --now arch-update-tray.service
systemctl --user enable --now arch-update.timer

# GNOME
sudo pacman -S firefox gimp libreoffice-fresh evolution file-roller dconf-editor gnome-themes-extra gnome-browser-connector gst-plugin-pipewire adw-gtk-theme gst-plugins-base gst-plugins-bad gst-plugins-good gst-plugins-ugly gst-libav qt5ct

yay adwaita-qt5 adwaita-qt6 qadwaitadecorations-qt5 qadwaitadecorations-qt6

nano ~/.profile
export QT_QPA_PLATFORMTHEME="qt5ct"

nano ~/.bash_profile
[[ -f ~/.profile ]] && . ~/.profile

# KDE
sudo pacman -S firefox krita kmail libreoffice-fresh gst-plugin-pipewire gst-plugins-base gst-plugins-bad gst-plugins-good gst-plugins-ugly gst-libav sddm-kcm qt5-declarative breeze-gtk kde-gtk-config 
