1. install HDD smart tools:
sudo apt-get install smartmontools 

install gsmartcontrol
sudo apt install gsmartcontrol

2. list drives:
sudo fdisk -l

3. list status:
sudo smartctl -i /dev/xxx

4. wipe disk, blocks of 1M. this should allow disk to remap bad sectors if reserve sectors still are:
sudo dd if=/dev/zero of=/dev/xxx bs=1M
(should take about 2 hours)
