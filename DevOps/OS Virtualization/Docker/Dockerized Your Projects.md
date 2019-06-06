# Dockerized Your Projects

## On the Development

### 1 Network

- Create a separate docker network and give your desire IP address pool or list.

- Note this process will only be executed once.

```txt
Using docker network create --driver=bridge --subnet=<192.168.x.x/16> <docker-bridge-local>
```

### 2 Dockerfile

- Create your Dockerfile and include all the necessary libraries or packages that will support the desire project you want to build.

- You can get online: [knowledge/DevOps/OS Virtualization/Docker/Docker Files at master · LordDashMe/knowledge · GitHub](https://github.com/LordDashMe/knowledge/tree/master/DevOps/OS%20Virtualization/Docker/Docker%20Files)

### 3 Images

- Once you have a Dockerfile you will build it and the name and tag will based on what the docker file you created extends from and the name of primary technology used in the docker file.

```txt
docker build --tag="<primary-technology>:<extends-from>" </dockerfile/location/path>
```

### 4 Compose

- Create your Docker Compose configuration. The Docker Compose helps to easily manipulate or provide a command to the Docker Engine.

```yml
version: '3.2'

networks:
  <your-custom-bridge-name>:
    external:
      name: '<your-external-custom-bridge-name>'

services:
  app:
    image: '<your-exiting-image>'
    volumes:
      - '</host/path/project/>:</container/path/project>'
    networks:
      <your-custom-bridge-name>:
        ipv4_address: '<192.168.x.x>'
    ports:
      - '<host-port>:<container-port>'
    tty: true
    stdin_open: true
    restart: 'no'
    container_name: '<your-container-name>'
```

- Once done you can now use the command inside the folder of each project inside the Docker Compose folder:

```txt
docker-compose up -d
```
