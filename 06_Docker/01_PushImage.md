###### Create dockerfile
###### Login Docker Hub
Docker ID needed. 
```bash
docker login --username=DockerID
```
###### Build Image
```bash
docker build -t DockerID/name of repo in DockerHUB:tag in DockerHUB repo .
```
###### Push Image to Docker HUB
```bash
docker push DockerID/name of repo in DockerHUB:tag in DockerHUB repo
```
Now image can be retrieved as needed.
```bash
FROM DockerID/name of repo in DockerHUB:tag in DockerHUB
```
