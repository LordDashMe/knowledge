# Docker Compose Example Format

```yml
version: '3.2'

networks:
  {your-custom-bridge-name}:
    external:
      name: {your-custom-bridge-name}

services:
  app:
    image: {your-exiting-image}
    volumes:
      - /var/www/site/{your-application}:/var/www/site
    external_links:
      - {your-existing-containers}
    networks:
      {your-custom-bridge-name}:
        ipv4_address: {your-ip-v4}
    ports:
      - {your-custom-port}
    command: /usr/sbin/apachectl -D FOREGROUND
    tty: true
    stdin_open: true
    restart: always
```
