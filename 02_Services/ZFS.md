1. make sure the drives are connected on motherboard in the order of that the controller presents.
install zfs:
sudo apt install zfsutils-linux 

2. list available disks and pools:
sudo fdisk -l
sudo zpool list

3. create mirror pool:
sudo zpool create -f -o ashift=12 <pool name> mirror /dev/sda /dev/sdb

check created pool:
sudo zpool status <pool name> 
sudo zfs get all 

4. create pool raid 0:
sudo zpool create -f -o ashift=12 <pool name> <device1> <device2>
sudo zpool create -f -o ashift=12 labo /dev/sda /dev/sdb

5. for proxmox:
after pool creation go to Datacenter/Storage and add the zfs volume.

list container images:
pveam update
pveam available --section system

download image:
pveam download local <image name>

connect:
ssh -l root 192.168.1.xxx

for OSs connect with Filezilla, SFTP using root to /var/lib/vz/template/iso the needed ISO.

6. delete all datasets or pool:
sudo zfs destroy -r <pool name>
sudo zpool destroy <pool name>

7. get pool speed:
sudo /usr/bin/time --verbose dd if=/dev/zero of=sometestfile bs=1024 count=30000

more: https://blog.programster.org/zfs-cheatsheet

8. stats:
zpool iostat -v
