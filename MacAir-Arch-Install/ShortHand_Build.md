# Build:

```
=======================
Enable fstrim for SSD ==
=======================

sudo systemctl enable fstrim.timer


===============
Set Time Zone ==
===============

--------------------------------
Find your time zone in the list:
--------------------------------

timedatectl list-timezones

--------------
Set time zone:
--------------

timedatectl set-timezone Zone/SubZone


Example:  For central time in the US you would use America/Chicago

=======================
Network related steps ==
=======================

------------------------------
Enable Network Manger service:
------------------------------

sudo systemctl start NetworkManger
sudo systemctl enable NetworkManager

----------------------
Install Wi-fi Drivers:
----------------------

Note:
I didn't have wifi connection after first install, installing packages below would fix that after reboot.  I used tethered connection for internet access till this step.


sudo pacman -S dkms broadcom-wl-dkms gnome-keyring

-----------------------------------------------
Using NetworkManager(nmcli) to connect to Wifi:
-----------------------------------------------

Check the Wifi list:
nmcli device wifi list

Connect to SSID:
sudo nmcli --ask dev wifi connect [SSID]


Note: The --ask flag will ask for the password and hide it instead of it being plain text in terminal.

================
Security Steps ==
================

I would recommend this, but there are other options:

-----------------
Install GUFW/UFW:
-----------------

sudo pacman -S gufw

-------------------------
Start/enable UFW service:
-------------------------

sudo systemctl start ufw
sudo systemctl enable ufw


Note:  I have noticed I have to open gufw and click enable and have the services start before a reboot will show that gufw is running in the GUI.

---------------
Install ClamAV:
---------------


sudo pacman -S clamav

-----------------
Install rkhunter:
-----------------

sudo pacman -S rkhunter

-----------------
Running rkhunter:
-----------------

rkhunter --propupd    <--This is really to be run when you first install
rkhunter --check --sk



====================
Install Yay and Pip==
====================

--------------------------------------------------------
Yay -This will allow you access to the AUR repositories:
--------------------------------------------------------

sudo pacman -S --needed git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

----
Pip:
----

sudo pacman -S python-pip

=======================
Install XORG and qtile==
=======================
----------------------------
Install XORG and your WM/DE:
----------------------------

sud pacman -S xorg-server xorg-xinit mesa brightnessctl kitty xf86-video-intel vulkan-intel qtile thunar udiskie ntfs-3g gvfs polkit-gnome

-------------------
Making qtile start:
-------------------

sudo echo "qtile start" >> ~/.xinitrc


Note:  Replace with chosen DE/WM within the quotes.  Many of the other DE/WM's use "exec i3" "exec kde" and so on.

===================
Starting the DE/WM==
===================

startx
```



