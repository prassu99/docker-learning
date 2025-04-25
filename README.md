# docker-learning
<h1>Learning Docker</h1>

```shell
#Check Docker version
docker --version
```
<img width="302" alt="image" src="https://github.com/user-attachments/assets/48bcdb82-4e54-49ec-9cdb-af5000aab415" />
<br>

```shell
#Run Hello world image
docker run hello-world
```
<img width="708" alt="image" src="https://github.com/user-attachments/assets/6d413a1f-3b3f-4496-b69a-3ae283930cc8" />

<br>

```shell
#See running containers
docker ps
```

```shell
#See all containers
docker ps -a
```

```shell
#See images
docker images
```

```shell
#Stop a docker container where c73cd6ffde7c is a container Id
docker stop c73cd6ffde7c
```


```shell
#Remove a docker container where c73cd6ffde7c is a container Id
docker rm c73cd6ffde7c
```


```shell
#Remove a docker image
docker rmi hello-world
```

```shell
#Removes all unused containers, networks, and dangling images.
docker system prune
```

