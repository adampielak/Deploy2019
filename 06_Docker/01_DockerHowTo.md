

##### 1. Prerequisites
- 64b os
- git <br />
- check:
```html
https://docs.docker.com/install/linux/docker-ce/ubuntu/
```
- set docker data location by editing /etc/docker/daemon.json
```json
{
    "data-root": "/mnt/docker-data",
    "storage-driver": "overlay2"
}
```
##### 2. Download Docker
```bash
wget https://download.docker.com/linux/static/stable/x86_64/docker-18.09.4.tgz
```
Extract file:
```bash
tar -xzvf <downloaded docker archive>
```
##### 3. Copy to bin
```bash
sudo cp docker/* /usr/bin/
```
##### 4. Make current user not use sudo
```bash
sudo usermod -aG docker $USER
 ```
After full logout change will take place.
##### 5. Start Docker daemon
```bash
# check first
systemctl show --property ActiveState docker
sudo dockerd &
```
##### 6. Create docker file
```bash
vi basex.dok
# ex.
# Dockerfile
# FROM basex/basexhttp:9.1
```
##### 7. Create docker image based on a docker file
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
##### 8. Create container based on created image
###### Create network using macvlan driver to connect from other host
```bash
docker network create -d macvlan --subnet=192.168.1.0/24 --ip-range=192.168.1.128/25 --gateway=192.168.1.127 -o parent=enp4s0 macnet
# list networks
docker network ls
# inspect network
docker network inspect <network name>
```
```bash
sudo docker run -d -p 5432:5432 --name container_name -ti {image ID}
# or
sudo docker run -d -p 5432:5432 --name container_name --network <network name> -ti {image ID}
# check
sudo docker ps -a
```
##### 9. Container Operations
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
##### 10. Attach to container. 
Detach with ctrl + D - container will stop at detach:
```bash
docker attach <container ID>
```
##### 11. Delete all containers:
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
