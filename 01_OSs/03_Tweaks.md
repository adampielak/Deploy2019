# Tweaks <a name="top"></a> <a name="top"></a>
* [OS Version](#vers)
* [X Type](#x)
* [Grep](#grep)
* [GB Written](#written)
* [LOC](#loc)
* [MOTD](#motd)
* [New hard drive](#new)
* [Partitioning](#format)
* [Mount Disk](#mount)
* [No sleep when docked](#dock)
* [Running Services](#services)
* [Other Tweaks](#other)

## OS Version <a name="vers"></a> 
```bash
cat /etc/*-release
```
## X Type <a name="x"></a> ([Up](#top))
```bash
ls /usr/bin/*session
```
## Grep <a name="grep"></a> ([Up](#top))
```bash
grep -rnw '/path/to/somewhere/' -e 'pattern'
# -r or -R is recursive,
# -n is line number,
# -w stands for match the whole word,
# -l (lower-case L) can be added to just give the file name of matching files.
```
## GB Written <a name="written"></a> ([Up](#top))
```bash
sudo smartctl -A /dev/sda | awk '/^241/ { print "GBW: "($10 * 1024) * 1.0e-5, "GB" } '
```
## Lines of Code <a name="loc"></a> ([Up](#top))
```bash
sudo apt install cloc
```
Make script cloc-git and place in path, chmod +x:
```bash
#!/usr/bin/env bash
git clone --depth 1 "$1" temp-linecount-repo &&
  printf "('temp-linecount-repo' will be deleted automatically)\n\n\n" &&
  cloc temp-linecount-repo &&
  rm -rf temp-linecount-repo
```
Usage
```bash
cloc-git https://github.com/evalEmpire/perl5i.git
```
## Update MOTD <a name="motd"></a> ([Up](#top))
```bash
cd /etc/update-motd.d
sudo mkdir _scripts
sudo mv needed scripts to _scripts
```
## Add New hard drive to OS <a name="new"></a> ([Up](#top))
```bash
sudo parted # partition drive
lsblk       # identify drive
sudo parted /dev/sdx mklabel gpt  # create partition table on drive
sudo parted -a opt /dev/sdx mkpart primary ext4 0% 100%  # create partition
lsblk       # check partition
```
## Partitioning <a name="format"></a> ([Up](#top))
### Create Partition
```bash
fdisk /dev/sdc
# create new gpt label
# create new partition <n>
```
### Format Partition
```bash
sudo mkfs.ext4 -L datapartitionlabel /dev/sdX1
```
## Permanently mount disk <a name="mount"></a> ([Up](#top))
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
## Prevent laptop going to sleep when docked <a name="dock"></a> ([Up](#top))
```bash
sudo vi /etc/systemd/logind.conf
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
# save run below and test
sudo service systemd-logind restart
```
## Check all running services <a name="services"></a> ([Up](#top))
```bash
service --status-all
systemctl --type=service --state=active list-units
```
## Other Tweaks <a name="other"></a> ([Up](#top))
```html
https://dev.to/javinpaul/10-simple-linux-tips-which-save-50-of-my-time-in-the-command-line-4moo?utm_source=digest_mailer&utm_medium=email&utm_campaign=digest_email
```
