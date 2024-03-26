# Build:

Enable fstrim for SSD -
----

+ Run
```
sudo systemctl enable fstrim.timer
```

Set Time Zone -
---

Find your time zone in the list:

+ Run
```
timedatectl list-timezones
```

Set time zone:

+ Run
```
timedatectl set-timezone Zone/SubZone
```

Example:  For central time in the US you would use America/Chicago

Network related steps -
----

Enable Network Manger service:
+ Run
```
sudo systemctl start NetworkManger
sudo systemctl enable NetworkManager
```
Install Wi-fi Drivers:

Note:
I didn't have wifi connection after first install, installing packages below would fix that after reboot.  I used tethered connection for internet access till this step.

+ Run
```
sudo pacman -S dkms broadcom-wl-dkms gnome-keyring
```

Using NetworkManager(nmcli) to connect to Wifi:

+ Run

```
Check the Wifi list:
nmcli device wifi list

Connect to SSID:
sudo nmcli --ask dev wifi connect [SSID]
```

Note: The --ask flag will ask for the password and hide it instead of it being plain text in terminal.


Security Steps -
----

I would recommend this, but some may see it as over kill:

Install GUFW/UFW:

+ Run
```
sudo pacman -S gufw
```

Start/enable UFW service:

+ Run
```
sudo systemctl start ufw
sudo systemctl enable ufw
```

Note:  I have noticed I have to open gufw and click enable and have the services start before a reboot will show that gufw is running in the GUI.

Install ClamAV:

+ Run
```
sudo pacman -S clamav
```

Install rkhunter:

+ Run
```
sudo pacman -S rkhunter
```

Running rkhunter:

+Run
```
rkhunter --propupd    <--This is really to be run when you first install
rkhunter --check --sk
```



Install Yay and Pip-
----

Yay -This will allow you access to the AUR repositories:

+ Run
```
sudo pacman -S --needed git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

Pip -

+ Run
```
sudo pacman -S python-pip
```

Install XORG and qtile:
---

Install XORG and your WM/DE:

+ Run
```
sud pacman -S xorg-server xorg-xinit mesa brightnessctl kitty xf86-video-intel vulkan-intel qtile thunar udiskie ntfs-3g gvfs polkit-gnome
```

Making qtile start:

+ Run
```
sudo echo "qtile start" >> ~/.xinitrc
```

Note:  Replace with chosen DE/WM within the quotes.  Many of the other DE/WM's use "exec i3" "exec kde" and so on.

Starting the DE/WM:

+ Run
```
startx
```



