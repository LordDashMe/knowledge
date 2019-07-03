# Docker Compose Example Format

```yml
version: '3.2'

networks:
  <your-docker-network-name>:
    external:
      name: '<your-docker-network-name>'

services:
  app:
    image: '<your-existing-image>'
    volumes:
      - '</host/path/project/>:</container/path/project>'
    networks:
      <your-docker-network-name>:
        ipv4_address: '<you-docker-network-ip-address ex. 192.168.x.x>'
    ports:
      - '<host-port>:<container-port>'
    tty: true
    stdin_open: true
    restart: 'no'
    container_name: '<your-container-name>'
```
