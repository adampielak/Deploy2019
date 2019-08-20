##### Create Alpine latest container
```bash
docker pull alpine
docker run -it --rm alpine # /bin/ash, defaults to sh
# -i , interactive mode
# -t , alocte pseudo TTY
# --rm , remove container after stop
```
##### Detaching from container 
Ctrl-P Ctrl-Q
