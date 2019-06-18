1. disable admin user access from outside

2.
/ip firewall nat
add chain=srcnat out-interface=outside action=masquerade

3.
https://wiki.mikrotik.com/wiki/Manual:Securing_Your_Router
https://wiki.mikrotik.com/wiki/Bruteforce_login_prevention

4. traffic shaping for internet testing
see: https://wiki.mikrotik.com/wiki/Manual:Queue

/queue simple 
add name=checkpoor target=192.168.1.0/24 max-limit=64K/64K 
add name=checkaverage target=192.168.1.0/24 max-limit=128K/128K 