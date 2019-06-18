1. Install container packages:
```bash
sudo apt install lxc bridge-utils
```

2. Create bridge interface:
* identify physical interface that will be used by the bridge:
```bash
sudo vi /etc/network/interfaces
```
* create the bridge in /etc/network/interfaces:
```bash
# The primary network interface. Will be brought up by bridge
iface ens18 inet manual

# bridge
auto lxcbr0
iface lxcbr0 inet dhcp
    bridge_ports ens18
```
* restart network service to load new configuration
```bash
sudo service networking restart
```

3. Configure lxc process:
```bash
sudo vi /etc/default/lxc-net 

USE_LXC_BRIDGE="true"
LXC_BRIDGE = "lxcbr0"
```

4. Configure default container configuration:
```bash
sudo vi /etc/lxc/default.conf

lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:xx:xx:xx
```

* restart lxc service:
```bash
sudo service lxc-net restart
```

* container configuration in:
```bash
/var/lib/lxc/<container>/config
```

* create container:
```bash
sudo lxc-create -n c001 -t debian -- -r stretch
```

* attach as root to container:
```bash
sudo lxc-start -n c001
sudo lxc-attach -n c001
```

* occupied space by container:
```bash
sudo du -sh /var/lib/lxc/c001
```

* copy container (c001 must be stopped):
```bash
sudo lxc-copy -n c001 -N c002
```

* tests in container:
```bash
apt install inetutils-ping
```
