# Docker Compose Example Format

```yml
version: '3.2'

networks:
  [[Your custom bridge name]]:
    external:
      name: [[Your custom bridge name]]

services:
  app:
    image: [[Your exiting image]]
    volumes:
      - /var/www/site/[[Your application]]:/var/www/site
    external_links:
      - [[Your existing containers]]
    networks:
      [[Your custom bridge name]]:
        ipv4_address: [[Your ip v4]]
    ports:
      - [[Your custom port]]
    command: /usr/sbin/apachectl -D FOREGROUND
    tty: true
    stdin_open: true
    restart: always
```
