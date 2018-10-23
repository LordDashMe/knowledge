# Basic Docker Commands

- Execute Interactive Terminal in a container.

  - <https://stackoverflow.com/questions/20932357/docker-enter-running-container-with-new-tty>

  - <https://docs.docker.com/engine/reference/commandline/exec/>

```text
docker exec -it [container-id] bash
```

- Show all the registered container.

```text
docker ps --all
```

- Remove a specific container.

```text
docker rm [container id]
```

- Show all the registered images.

```text
docker images
```

- Build an image.

```text
docker build --tag=[image-name:tag-version] [/path]
```

- Remove a specific image.

```text
docker rmi [optional -f] - this will force delete the image
```

- Run a MySQL container with password constant.

  - <https://stackoverflow.com/questions/33299303/how-to-build-a-docker-container-with-a-running-mysql?noredirect=1>

```text
docker run --name [some-mysql] -e MYSQL_ROOT_PASSWORD=[my-secret-pw] -d [mysql:tag]
```

- Run a container.

  - <https://docs.docker.com/engine/reference/commandline/run/#add-host-device-to-container-device>

```text
docker run -i -t -p [8080:80] [ubuntu:latest]
```

- Stop all the registered containers.

```text
docker stop $(docker ps -a -q)
```

- Remove all the registered containers.

```text
docker rm $(docker ps -a -q)
```

- Show the docker events in the server.

  - <https://docs.docker.com/engine/reference/commandline/events/#format-the-output>

```text
docker events
```

- Show the docker logs in the server.

```text
docker logs
```
