###### 1.Disable admin user access from outside

###### 2.Configure NAT
/ip firewall nat
add chain=srcnat out-interface=outside action=masquerade

###### 3.Secure Router
```html
https://wiki.mikrotik.com/wiki/Manual:Securing_Your_Router
https://wiki.mikrotik.com/wiki/Bruteforce_login_prevention
```
###### 4. Traffic shaping for internet testing
```html
https://wiki.mikrotik.com/wiki/Manual:Queue
```
```bash
/queue simple 
add name=checkpoor target=192.168.1.0/24 max-limit=64K/64K 
add name=checkaverage target=192.168.1.0/24 max-limit=128K/128K 
```
