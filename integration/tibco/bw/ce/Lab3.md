---
title: Lab 3
description: 
published: true
date: 2021-04-16T08:06:23.828Z
tags: 
editor: markdown
dateCreated: 2021-04-08T13:08:34.367Z
---

# Managing the filsystem
The files to test the application are available at the following link: https://drive.google.com/open?id=185i9v15uf4U5BkmzWaLdtxp-Bl73IyW0

Useful Links: https://docs.docker.com/storage/volumes/

At the filesystem level, each container is completely isolated from the underlying system and from that of all other containers. For this reason, when you want to access a file on the host from the container, you need to use the volume drivers.
  
![lab3.1.png](/bwce/lab3.1.png)

Let's create a Studio application that reads the file.txt  on the host and writes its contents to the fileModified.txt. Finally, every time the fileModified.txt is written, we notify through a filePoller.

![lab3.2.png](/bwce/lab3.2.png)

![lab3.3.png](/bwce/lab3.3.png)

![lab3.4.png](/bwce/lab3.4.png)

On Linux: 
1. 	we create the readFile directory and insert the .ear file and the Dockerfile
1. create the image: **docker build -t bwce / readfile.**
1. create in the root a directory called condivisaDocker, which will contain the file.txt to read

To mount a specific directory located on your host as a Docker volume inside the container, add the following argument to the docker run command:
```
-v [host directory]:[container directory]
```
The host_directory and continer_directory are the absolute paths.  According to the example, the run command will be: 

```
docker run --name bwce-filesystem -v /condivisaDocker:/hostVolume bwce/readfile
```

Once run, we inspect the container to make sure the container directory has been created correctly. To do so we need to launch the following command: 
```
docker exec -it bwce-filesystem /bin/bash
```

![lab3.5.png](/bwce/lab3.5.png)

Accessing the hostVolume directory we will see the file.txt and fileModified.txt

![lab3.6.png](/bwce/lab3.6.png)