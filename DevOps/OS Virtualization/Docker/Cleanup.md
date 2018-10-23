# Cleanup

- Once in a while, you may need to cleanup resources (containers, volumes, images, networks).

- Delete volumes.

  - <https://github.com/chadoe/docker-cleanup-volumes>

```text
docker volume rm $(docker volume ls -qf dangling=true)
docker volume ls -qf dangling=true | xargs -r docker volume rm
```

- Delete networks.

```text
docker network ls  
docker network ls | grep "bridge"
docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')
```

- Remove docker images.

  - <http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images>

```text
docker images
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)

docker images | grep "none"
docker rmi $(docker images | grep "none" | awk '/ / { print $3 }')
```

- Remove docker containers.

  - <http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images>

```text
docker ps
docker ps -a
docker rm $(docker ps -qa --no-trunc --filter "status=exited")
```

- Resize disk space for docker vm.

```text
docker-machine create --driver virtualbox --virtualbox-disk-size "40000" default
```
