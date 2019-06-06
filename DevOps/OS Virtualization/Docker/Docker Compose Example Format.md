# Docker Compose Example Format

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
