# Arch-Termux-KDE-Plasma
Dis is a guide to get plasma KDE working on Termux arch Linux 

So first we need to see if all pkgs are up-to-date, getting proot-distro and getting arch Linux in it.
```bash
pkg update && pkg upgrade && pkg install proot-distro && proot-distro install archlinux && pd login archlinux --shared-tmp
```
ok now in arch we need to update all pkgs, we can do that by executing
```bash
pacman -Syu --noconfirm
```
now we need to get the DE (Desktop Environment)
we need to run
```bash
pacman -S plasma-desktop tigervnc --noconfirm
```
now were gonna get the script working, just paste these lines by order:
```bash
cat > ~/plasma.sh << 'EOF'
```
```bash
#!/bin/bash
pkill -f Xvnc; pkill -f plasmashell; pkill -f kwin; sleep 2; dbus-uuidgen > /etc/machine-id; Xvnc :2 -geometry 1920x1080 -rfbport 5902 -rfbauth ~/.vnc/passwd & sleep 3; export DISPLAY=:2; export DBUS_SESSION_BUS_ADDRESS=$(dbus-daemon --session --fork --print-address); startplasma-x11 &
EOF
```
```bash
chmod +x ~/plasma.sh
```
ok now we need to run the script, heres the cmd:
```bash
bash plasma.sh
```
And BOOM! A Plasma-KDE DE on ur phone! Now u can say: "Oh i use Arch btw"
Anyways yapped too much so cya! :) (NOTE: U need a vncviewer for this, i recommend bVNC free, u can get it on the play store. In bVNC u need to click the monitor with the + icon. Then u need to type in the "VNC Server" 
```bash
127.0.0.1
```
For the port type in
```bash
5902
```
and then for the "VNC Password" section go to ur arch terminal, type
```bash
vncpasswd
```
then type ur password in. Then in the "VNC Password" section type the password u made in arch linux.)
