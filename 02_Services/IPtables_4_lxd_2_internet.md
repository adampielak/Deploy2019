# Generated by iptables-save v1.6.0 on Wed Oct 11 14:47:33 2017
*nat
:PREROUTING ACCEPT [40:6489]
:INPUT ACCEPT [4:1035]
:OUTPUT ACCEPT [159:12563]
:POSTROUTING ACCEPT [159:12563]
-A POSTROUTING -s 192.168.1.0 ! -d 192.168.1.0  -m comment --comment "generated for LXD network lxdbr0" -j MASQUERADE
COMMIT
# Completed on Wed Oct 11 14:47:33 2017
# Generated by iptables-save v1.6.0 on Wed Oct 11 14:47:33 2017
*mangle
:PREROUTING ACCEPT [2033:118428]
:INPUT ACCEPT [1996:112890]
:FORWARD ACCEPT [2:168]
:OUTPUT ACCEPT [1277:106729]
:POSTROUTING ACCEPT [1279:106897]
-A POSTROUTING -o newlxdbr0 -p udp -m udp --dport 68 -m comment --comment "generated for LXD network lxdbr0" -j CHECKSUM --checksum-fill
COMMIT
# Completed on Wed Oct 11 14:47:33 2017
# Generated by iptables-save v1.6.0 on Wed Oct 11 14:47:33 2017
*filter
:INPUT ACCEPT [1992:112103]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1273:105855]
-A INPUT -i lxdbr0 -p tcp -m tcp --dport 53 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A INPUT -i lxdbr0 -p udp -m udp --dport 53 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A INPUT -i lxdbr0 -p udp -m udp --dport 67 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A FORWARD -o lxdbr0 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A FORWARD -i lxdbr0 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A OUTPUT -o lxdbr0 -p tcp -m tcp --sport 53 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A OUTPUT -o lxdbr0 -p udp -m udp --sport 53 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
-A OUTPUT -o lxdbr0 -p udp -m udp --sport 67 -m comment --comment "generated for LXD network lxdbr0" -j ACCEPT
COMMIT
# Completed on Wed Oct 11 14:47:33 2017
