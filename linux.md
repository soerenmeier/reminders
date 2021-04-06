
## Custom Systemd Service

```

```

## Create bootable stick
find drive with `lsblk` command. without the number for example `sda`  
Now use the following:
```
sudo dd bs=4M if=<iso-file> of=/dev/<name in lsblk> conv=fdatasync status=progress
```

## Mount Network drive
Install `cifs-utils`.  
Show smb servers:
```
smbclient -L <host>
```
Setup cifs:
```
sudo mount -t cifs -o username=<username> //<server ip>/<path> <mount path>
```

## create iso
link: [thomas-krenn.com](https://www.thomas-krenn.com/de/wiki/ISO_Image_von_CD_oder_DVD_unter_Linux_erstellen)
Install package `genisoimage`.  
Get `Logical block size` and `Volume size`:
```
sudo isoinfo -d -i /dev/cdrom | grep -i -E 'block size|volume size'
```
Now clone the drive:
```
dd if=/dev/cdrom of=<iso location> bs=<block size> count=<volume size> status=progress
```