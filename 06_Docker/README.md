### Debian 10 Installation
##### 1. Prerequisites
- 64b os
- RAM disk
- check:
```html
https://computingforgeeks.com/install-docker-and-docker-compose-on-debian-10-buster/
https://docs.docker.com/install/linux/docker-ce/ubuntu/
https://flaviocopes.com/golang-docker/
```
- set docker data location by editing /etc/docker/daemon.json
```json
{
    "data-root": "/mnt/tmpfs.ramdisk/docker-data",
    "storage-driver": "overlay2"
}
```
reload cnfiguration:
```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
systemctl show --property=Environment docker
```
##### 2. Install dependencies
```bash
sudo apt update
sudo apt -y install apt-transport-https ca-certificates curl gnupg2 software-properties-common
```
##### 3. Add GPG key
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```
##### 4. Add Docker repo
```bash
sudo vi /etc/apt/sources.list
# add at end of file: deb [arch=amd64] https://download.docker.com/linux/debian buster stable
sudo apt update
```
##### 5. Install Docker
```bash
sudo apt -y install docker-ce
```
###### Install Docker Compose
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```
##### 6. Make current user not use sudo
Change will take place after full logout / log off.
```bash
sudo usermod -aG docker $USER  # $USER is environment variable holding current user
 ```
##### 7. Start Docker daemon
```bash
# check first
systemctl show --property ActiveState docker
sudo dockerd &
```
##### 8. Create docker file
```bash
vi basex.dok
# ex.
# Dockerfile
# FROM basex/basexhttp:9.1
```
##### 9. Create docker image based on a docker file
```bash
sudo docker build - < Dockerfile
```
- Check newly created image:
```bash
docker images -a
docker history <img ID>
```
- Delete image (untagged):
```bash
docker images -q |xargs docker rmi -f
# or
docker rmi <img ID>
```
##### 10. Create container based on created image
###### Create network using macvlan driver to connect from other host
```bash
docker network create -d macvlan --subnet=192.168.1.0/24 --ip-range=192.168.1.128/25 --gateway=192.168.1.127 -o parent=enp4s0 macnet
# list networks
docker network ls
# inspect network
docker network inspect <network name>
```
```bash
sudo docker run -d -p 5432:5432 --name container_name -it {image ID}
# -i , interactive mode
# -t , alocate pseudo TTY
# or
sudo docker run -d -p 5432:5432 --name container_name --network <network name> -it {image ID}
# check
sudo docker ps -a
```
##### 11. Container Operations
###### Start container
```bash
docker start <container ID>
```
###### Stop container
```bash
docker stop <container ID>
```
###### Get container IP
```bash
docker inspect <container ID> | grep IPAddress
```
###### Remove container
```bash
docker rm <container ID>  # -f (force) if container is active
```
###### List containers
```bash
docker ps -a
```
###### Execute command container
```bash
docker exec -it <container name> <command, ex. bash>
```
###### Get container IP
```bash
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}'  container_name_or_id
```
##### 12. Attach to container. 
Detach with ctrl + D - container will stop at detach:
```bash
docker attach <container ID>
```
##### 13. Delete all containers:
```bash
docker rm -f `docker ps --no-trunc -aq`
```
Notes:
- -d , Run container in background and print container ID
- -p , Publish a container’s port(s) to the host
- -t , Allocate a pseudo-TTY
- -i , Keep STDIN open even if not attached 
- https://docs.docker.com/engine/installation/linux/docker-ce/binaries/#prerequisites
- add current user to docker group to run without sudo. logout and login to take effect:
```bash
sudo usermod -aG docker <user_to_add>
```
Port exposing:
The EXPOSE instruction does not actually publish the port. 
It functions as a type of documentation between the person who builds the image and the person who runs the container,
about which ports are intended to be published. 
To actually publish the port when running the container, use the -p flag on docker run to publish and map one or more 
ports, or the -P flag to publish all exposed ports and map them to high-order ports.

https://docs.docker.com/engine/examples/running_ssh_service/

##### Troubleshoot
Masked docker service:
a. unmask 
```bash
systemctl unmask docker.service
systemctl unmask docker.socket
systemctl start docker.service
# now the service should appear enabled
systemctl list-unit-files | grep docker
```

##### Rancher and K8
```html
https://www.youtube.com/watch?v=sMSvjz-hyiA
```
##### K8
```html
https://towardsdatascience.com/key-kubernetes-commands-741fe61fde8
```
##### Resources
```html
http://containertutorials.com/index.html
https://medium.com/@betz.mark/ten-tips-for-debugging-docker-containers-cde4da841a1d
https://medium.com/@chemidy/create-the-smallest-and-secured-golang-docker-image-based-on-scratch-4752223b7324
```
