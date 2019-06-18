sudo parted /dev/sdb
check: print
create new allocation table: mklabel gpt

create new partition: mkpart
with options: partition type ext4 start: 1 end: -1 

exit parted: quit
sudo mkfs.ext4 /dev/sdb1
mount: sudo mount /dev/sdb1 /media/usb_drive/

add to fstab for permanent mount. get UUID with blkid:
sudo vi /etc/fstab
UUID=2fac23fe-9e9e-4e83-911d-7b4daa2f5e47 /media/usb_drive/ ext4        defaults 0 0
