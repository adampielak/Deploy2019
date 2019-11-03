### For Windows ISO (UEFI boot BIOS):

```bash
sudo apt install extlinux

curl -L https://git.io/bootiso -O
chmod +x bootiso
sudo ./bootiso <image.iso>
```

### For Linux ISO:
```html
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-10.1.0-amd64-netinst.iso
```
```bash
https://www.balena.io/etcher/
sudo ./balena AppImage
```

### Linux CLI
```bash
sudo dd if=[path_to_iso] of=[path_to_usb]
# example
sudo dd if=/home/slick/Downloads/debian-7.4.0-amd64-CD-1.iso of=/dev/sdb
```

### Linux Partitioning
```bash
sudo mkfs.ntfs /dev/sdc1
```
