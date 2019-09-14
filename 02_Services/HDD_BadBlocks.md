##### Install HDD smart tools:
```bash
sudo apt install smartmontools 
```
install gsmartcontrol
sudo apt install gsmartcontrol

##### List drives:
```bash
sudo fdisk -l
```
##### List status:
```bash
sudo smartctl -i /dev/sdx
```

##### Wipe disk,
In blocks of 1M, this should allow disk to remap bad sectors if reserve sectors still are:
```bash
sudo dd if=/dev/zero of=/dev/xxx bs=1M # should take about 2 hours
```
