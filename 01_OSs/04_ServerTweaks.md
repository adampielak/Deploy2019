Get OS version:
```bash
cat /etc/*-release
```
### 1. Update MOTD
```bash
cd /etc/update-motd.d
sudo mkdir _scripts
sudo mv needed scripts to _scripts
```
### 2. Add new hard drive to OS
```bash
sudo parted # partition drive
lsblk       # identify drive
sudo parted /dev/sdx mklabel gpt  # create partition table on drive
sudo parted -a opt /dev/sdx mkpart primary ext4 0% 100%  # create partition
lsblk       # check partition
```
### 3. Format partition
```bash
sudo mkfs.ext4 -L datapartitionlabel /dev/sdX1
```
### 4. Permanently mount disk
```bash
sudo lsblk --fs # get UUID
sudo vi /etc/fstab
# add partition, see https://en.wikipedia.org/wiki/Fstab
UUID=xxxxxxx /home/xxx/diskx ext4 defaults 0 2
```
If mount folder does not exist it will be created. Save. reboot and verify with 
```bash
df -h  # or
sudo fdisk /dev/sdx  # and p
# https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux
```
### 5. Prevent laptop going to sleep when docked
```bash
sudo vi /etc/systemd/logind.conf
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
# save run below and test
sudo service systemd-logind restart
```
### 6. Check all running services
```bash
service --status-all
systemctl --type=service --state=active list-units
```
