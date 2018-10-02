# Basic Docker Commands

## Docker Container Run

```text
docker exec -it [container-id] bash
```

<https://stackoverflow.com/questions/20932357/docker-enter-running-container-with-new-tty>

<https://docs.docker.com/engine/reference/commandline/exec/>

## Docker Show Container All

```text
docker ps --all
```

## Docker Remove Container

```text
docker rm <container id>
```

## Docker Images All

```text
docker images
```

## Docker Build Image

```text
docker build --tag={} /path
```

## Docker Remove Image

```text
docker rmi {-f} - this will force delete the image
```

## Docker Run Mysql

```text
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
```

<https://stackoverflow.com/questions/33299303/how-to-build-a-docker-container-with-a-running-mysql?noredirect=1>

## Docker Run

```text
docker run -i -t -p 8080:80 ubuntu:latest
```

<https://docs.docker.com/engine/reference/commandline/run/#add-host-device-to-container-device>

## Docker Stop All Containers

```text
docker stop $(docker ps -a -q)
```

## Docker Remove All Containers

```text
docker rm $(docker ps -a -q)
```

## Docker Events

```text
docker events&
```

## Docker Logs

```text
docker logs
```