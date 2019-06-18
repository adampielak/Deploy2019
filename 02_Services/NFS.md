1. install server:
apt install nfs-common nfs-kernel-server

2. install client
apt install nfs-common 

3. run server
check NFS socket is opened:
rpcinfo -p | grep nfs

check NFS file system is supported:
modprobe nfs
cat /proc/filesystems | grep nfs  - should return nfs or nfs4

mkdir /home/nfs
touch /home/nfs/xxx

vi /etc/exports
add:
/home/nfs/ (ro,sync)

load configuration:
service nfs-kernel-server restart

4. run client
mount locally:
mkdir /home/nfs_local 

mount <server IP>:/home/nfs /home/nfs_local 

mount permanently:
vi /etc/fstab
add:
<server IP>:/home/nfs /home/nfs_local/ nfs defaults 0 0 
