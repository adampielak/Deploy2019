### For Windows ISO (UEFI boot BIOS):

```bash
sudo apt install extlinux

curl -L https://git.io/bootiso -O
chmod +x bootiso
sudo ./bootiso <image.iso>
```

### For Linux ISO:
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
