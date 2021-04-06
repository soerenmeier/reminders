
## Flash Linux
Use Raspberry Pi Imager

## Pinout

## SSH
Create an empty file called `ssh` in the boot drive.

## WLAN
create a file called `wpa_supplicant.conf` in the boot drive.  
With the content:
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=2
country=CH

network={
    ssid="<>"
    psk="<>"
}
```

## Touch Screen
[raspberrypi doc](https://www.raspberrypi.org/documentation/hardware/display/README.md)

### Rotate 180deg
edit /boot/config.txt
```
lcd_rotate=2
```

## Login
```
user: pi
password: raspberry
```

## Chromium

Install necessary packages.
```
sudo apt install xserver-xorg x11-xserver-utils xinit chromium
```
Update 
```
sudo nano /etc/X11/Xwrapper.config
```
```
allowed_users=anybody
needs_root_rights=yes
```
file: chromium --window-size=800,480 --window-position=0,0 --disable-infobars --kiosk --app=\"http://{}\"
startx {file} -- -nocursor

```