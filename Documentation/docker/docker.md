# Docker Commands

[Back](../Documentation.md)

## Images

### Get docker image

```shell
docker pull <image>
```

> \<image> is the name of the image you want to get  

### List all docker images

```shell
docker image ls
```

### Delete image

```shell
docker rmi <image>
```

> \<image> is the name/id of the image you want to get  

---

## Containers

### List all docker containers running

```shell
docker ps
```

> tag `-a` for all containers (even stopped ones)  

### Create a container

```shell
docker create <image>
```

> \<image> is the name of the image you want to use  

### Delete container

```shell
docker rm <container>
```

> \<container> is the name/id of the container you want to get  

### Start a container

```shell
docker start <container>
```

> \<container> is the name/id of the container you want to start  

### Stop a container

```shell
docker stop <container>
```

> \<container> is the name/id of the container you want to stop  

### Run a container

run = create + start

```shell
docker run <tags> <image/container>
```

> <image/container> is the name/id of the image/container you want to run  
> tag `-d` for detached mode  
> tag `-p <host_port>:>container_port>` to map ports  
> tag `--name <name>` to name the container  
> tag `-e <variable>=>value>` to set an evironment variable  
> tag `--net <network>` to run the container on a specific network  
> `\` for multiline commands

---

## Debug

### Logs

```shell
docker logs <container>
```

> \<container> is the name/id of the running container

### Navigate container

```shell
docker exec -it <container> <command>
```

> \<container> is the name/id of the container you want to stop  
> \<command> is a command you want to run on the container  
>
> - `/bin/bash` or `/bin/sh` to get into the terminal

---

## Networking

### List docker networks

```shell
docker network ls
```

### Create docker network

```shell
docker network create <name>
```

> \<name> is the name of the network

---

## Dockerfile

Create a file called `Dockerfile`

```Dockerfile
FROM <image>:<tag>
ENV <variable1>=<value> \
    <variable2>=<value>
RUN <command>
COPY <host_app_path> <container_app_path>
WORKDIR <path>
CMD ["node", "index.js"]
```

> \<image> is a docker image  
> \<tag> is an image tag  
> \<command> is a linux command to run  
> the CMD line starts the application (node app example)  
> WORKDIR is a `cd`

### Build image from Dockerfile

```shell
docker build <tags> <path_Dockerfile>
```

> tag `-t <tagname>` \<tagname> is the name you want to tag the image with, `app:version`  
> \<path_Dockerfile> normally `.`

<!-- ## Docker Compose -->
