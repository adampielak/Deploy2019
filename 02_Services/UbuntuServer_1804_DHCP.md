sudo apt-get install isc-dhcp-server

configure ethernet interface on which server will run:
sudo vim /etc/default/isc-dhcp-server

INTERFACESv4="enp0s25"

sudo vim /etc/dhcp/dhcpd.conf

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.110;
}

restart daemon to take configuration:
sudo service isc-dhcp-server restart

verify server is up:
sudo netstat -uap
