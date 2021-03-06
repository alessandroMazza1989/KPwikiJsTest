---
title: 3.2
description: 
published: true
date: 2021-04-16T08:17:33.626Z
tags: 
editor: markdown
dateCreated: 2021-04-09T07:17:37.021Z
---

# Docker basic commands
Useful link: https://docs.docker.com/engine/reference/commandline/docker/
## **Docker build**
Build an image from a Dockerfile
```
docker build [OPTIONS] PATH | URL | -
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --file , -f    | Name of the Dockerfile (Default is 'PATH/Dockerfile')  |
| --force-rm   | Always remove intermediate containers  |
|  --tag , -t    | Name and optionally a tag in the 'name:tag' format |
## **Docker run**
Run a command in a new container
```
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
| --attach , -a    | Attach to STDIN, STDOUT or STDERR  |
|   --detach , -d     | Run container in background and print container ID  |
| --env , -e    | Set environment variables  |
|   --expose     | Expose a port or a range of ports  |
| --memory , -m  | Memory limit  |
| --mount    | Attach a filesystem mount to the container  |
|   --name     | Assign a name to the container  |
| --net | 	Connect a container to a network  |
| --rm    | Automatically remove the container when it exits  |
|   --volume , -v     | Bind mount a volume  |
## **Docker ps**
This command is used to list the running containers
```
docker ps [OPTIONS]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --all , -a    | Show all containers (default shows just running)  |
| --last , -n    | Show n last created containers (includes all states)  |

## **Docker exec**
Run a command in a running container
```
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --detach , -d    | Detached mode: run command in the background  |
| --env , -e   | Set environment variables  |
|   --interactive , -i    | Keep STDIN open even if not attached  |
| --tty , -t   | Allocate a pseudo-TTY  |

## **Docker stop**
Stop one or more running containers
```
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --time , -t    | Seconds to wait for stop before killing it  |
## **Docker kill**
Kill one or more running containers
```
docker kill [OPTIONS] CONTAINER [CONTAINER...]
```
## **Docker rm**
Remove one or more containers
```
 docker rm [OPTIONS] CONTAINER [CONTAINER...]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --force , -f   | Force the removal of a running container (uses SIGKILL)|
|--volumes , -v   | Remove anonymous volumes associated with the container  |
## **Docker rmi**
Remove one or more images
```
docker rmi [OPTIONS] IMAGE [IMAGE...]
```
**Useful Options**
| Name, shorthand  | Description |
| -------------    | ------------- |
|   --force , -f   | Force removal of the image|
| --no-prune   | Do not delete untagged parents  |
## **Docker version**
Show the Docker version information
```
docker version [OPTIONS]
```
