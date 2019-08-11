# Dockerized Your Projects

## On the Development

### Network

- Create a separate docker network and give your desire IP address pool or list.

- Note this process will only be executed once.

```txt
Using docker network create --driver=bridge --subnet=<192.168.x.x/16> <docker-bridge-local>
```

### Dockerfile

- Create your Dockerfile and include all the necessary libraries or packages that will support the desire project you want to build.

- You can check this example: [Docker Files](https://github.com/LordDashMe/knowledge/tree/master/DevOps/OS_Virtualization/Docker/Docker_Files)

### Images

- Once you have a Dockerfile you will build it and the name and tag will based on what the docker file you created extends from and the name of primary technology used in the docker file.

```txt
docker build --tag="<primary-technology>:<extends-from>" </dockerfile/location/path>
```

### Compose

- Create your Docker Compose configuration. The Docker Compose helps to easily manipulate or provide a command to the Docker Engine.

```yml
version: '3.2'

networks:
  compose-network:
    external:
      name: '<your-docker-network-name>'

services:
  app:
    image: '<your-existing-image>'
    volumes:
      - '</host/path/project/>:</container/path/project>'
    networks:
      compose-network:
        ipv4_address: '<you-docker-network-ip-address ex. 192.168.x.x>'
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
