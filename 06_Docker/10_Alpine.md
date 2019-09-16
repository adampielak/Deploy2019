##### Docker install in Alpine
```bash
vi /etc/apk/repositories  # uncomment community repo
apk update
rc-update add docker boot # adds docker daemon when booting
service docker start      # start docker service
```

##### Create container of Alpine latest 
```bash
docker pull alpine
docker run -it --rm alpine # /bin/ash, defaults to sh
# -i , interactive mode
# -t , alocate pseudo TTY
# --rm , remove container after stop
```
##### Detaching from container 
Ctrl-P Ctrl-Q
