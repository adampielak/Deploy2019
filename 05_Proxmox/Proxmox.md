1. Get Proxmox ISO. Install (needs UEFI)
```html
https://www.proxmox.com/en/downloads?task=callelement&format=raw&item_id=452&element=f85c494b-2b32-4109-b8c1-083cca2b7db6&method=download&args[0]=7b03f3ce48b75b7b5c4bbc322dfdb990
```
Connect to:
```html
https://192.168.1.6:8006/#v1:0:18:4::::::
```
2. Get container images with
```bash
pveam available
pveam download  local debian-9.0-standard_9.5-1_amd64.tar.gz # download container
pveam list local  # verify download
```
In case needed, to remove local image:
```bash
pveam remove local:vztmpl/alpine-3.7-default_20180913_amd64.tar.xz  
```
3. ISO images 
```bash
cd /var/lib/vz/template/iso  # see https://pve.proxmox.com/wiki/Storage:_Directory
```
4. Transfer image
```bash
scp debian-9.8.0-amd64-xfce-CD-1.iso root@192.168.1.100:/var/lib/vz/template/iso
```
5. Configure timezone
```bash
sudo dpkg-reconfigure tzdata
```
6. Move to no subscription repo
```bash
vi /etc/apt/sources.list.d/pve-enterprise.list # change to pve-no-subscription
```
7. Connect to container, attach to container from Proxmox shell:
```bash
lxc-attach --name <container ID>
# or
pct enter <container ID>
```
8. Modify ssh configuration to allow root to connect or use SSH key
```bash
vi /etc/ssh/sshd_config
service ssh restart
```
