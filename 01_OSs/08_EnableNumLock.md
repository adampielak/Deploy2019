#### Enable numlock after boot. 
See:
```html
https://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen
```
```bash
sudo apt install numlockx
sudo vi /etc/lightdm/lightdm.conf
# add line:
greeter-setup-script=/usr/bin/numlockx on
```
