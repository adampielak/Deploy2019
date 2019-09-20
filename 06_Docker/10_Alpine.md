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

##### Postgres in Alpine container
```bash
docker run --name P1 -d -p 5432:5432 -e POSTGRES_PASSWORD=pp postgres:alpine   # pulls image, creates container
docker exec <container ID> cat /etc/os-release  # ets OS version as Alpine
psql -h localhost -p 5432 -U postgres  # connects to DB
```

