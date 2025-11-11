  # **Docker commands**

| Command          | Description                     |
| ---------------- | ------------------------------- |
| `docker version` | Show Docker version information |
| `docker info`    | Display system-wide information |
| `docker login`   | Log in to a Docker registry     |
| `docker logout`  | Log out from a Docker registry  |
| `docker help`    | Show help for any command       |
 --------------
--------------------------------
 
## 1.docker attach - Attach local standard input/output to a running container

```bash
docker attach <container>
```

## 2. docker build - Build an image from a Dockerfile

```bash
docker build -t my-image .
```

## 3.docker commit - Create a new image from a container's changes

```bash
docker commit <container> new-image
```
## 4. docker cp - Copy files/folders between container and local filesystem

```bash
docker cp <container>:/path /local/path
```
## 5. docker create - Create a new container without starting it

```bash
docker create --name my-container nginx
```
## 6.docker diff - Inspect changes to files/directories on a container's filesystem

```bash
docker diff <container>
```

## 7. docker events - Get real-time events from the server

```bash
docker events
```
## 8.docker exec - Run a command in a running container

```bash
docker exec -it <container> bash
```
## 9 docker export - Export a container's filesystem as a tar archive

```bash
docker export <container> > container.tar
```

## 10. docker history - Show the history of an image

```bash
docker history <image>
```

## 11. docker help - Show help for any Docker command

```bash
docker help <command>
```

## 12. docker images - List images

```bash
docker images
```
## 13.docker import - Import the contents from a tarball to create a filesystem image

```bash
docker import container.tar new-image
```
docker info - Display system-wide information

bash
docker info
docker inspect - Return low-level information on Docker objects

bash
docker inspect <container>
K
docker kill - Kill one or more running containers

bash
docker kill <container>
L
docker load - Load an image from a tar archive or STDIN

bash
docker load -i image.tar
docker login - Log in to a Docker registry

bash
docker login
docker logout - Log out from a Docker registry

bash
docker logout
docker logs - Fetch the logs of a container

bash
docker logs <container>
N
docker network - Manage networks

bash
docker network ls
docker network create my-network
docker network inspect my-network
P
docker pause - Pause all processes within one or more containers

bash
docker pause <container>
docker port - List port mappings or a specific mapping for the container

bash
docker port <container>
docker ps - List containers

bash
docker ps          # Running containers
docker ps -a       # All containers
docker pull - Pull an image or a repository from a registry

bash
docker pull nginx
docker push - Push an image or a repository to a registry

bash
docker push my-image
R
docker rename - Rename a container

bash
docker rename old-name new-name
docker restart - Restart one or more containers

bash
docker restart <container>
docker rm - Remove one or more containers

bash
docker rm <container>
docker rm $(docker ps -aq)  # Remove all containers
docker rmi - Remove one or more images

bash
docker rmi <image>
docker run - Run a command in a new container

bash
docker run -d -p 80:80 --name my-nginx nginx
S
docker save - Save one or more images to a tar archive

bash
docker save -o image.tar <image>
docker search - Search Docker Hub for images

bash
docker search nginx
docker start - Start one or more stopped containers

bash
docker start <container>
docker stats - Display a live stream of container(s) resource usage statistics

bash
docker stats
docker stop - Stop one or more running containers

bash
docker stop <container>
T
docker tag - Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

bash
docker tag my-image:latest my-registry/my-image:v1.0
docker top - Display the running processes of a container

bash
docker top <container>
U
docker unpause - Unpause all processes within one or more containers

bash
docker unpause <container>
docker update - Update configuration of one or more containers

bash
docker update --memory 512m <container>
V
docker version - Show the Docker version information

bash
docker version
docker volume - Manage volumes

bash
docker volume ls
docker volume create my-volume
W
docker wait - Block until one or more containers stop, then print their exit codes

bash
docker wait <container>
Common Command Combinations
Container Management
bash
# Run a container in detached mode
docker run -d --name my-container -p 8080:80 nginx

# Run a container interactively
docker run -it ubuntu bash

# Execute command in running container
docker exec -it my-container bash

# View logs
docker logs -f my-container

# Stop and remove container
docker stop my-container && docker rm my-container
Image Management
bash
# Build image with tag
docker build -t my-app:latest .

# List images
docker images

# Remove unused images
docker image prune

# Remove all images
docker rmi $(docker images -q)
System Cleanup
bash
# Remove all stopped containers
docker container prune

# Remove all unused networks
docker network prune

# Remove all unused volumes
docker volume prune

# Remove all unused images, containers, networks
docker system prune

