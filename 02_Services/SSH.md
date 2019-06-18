ssh-keygen -t rsa -b 4096

copy file. run on source host:
scp file-to-send user@targethost:/path/to/place/file

works also for transfer to local host. run on remote host:
scp /path/to/file user@targethost:/path/to/place/file
