# Docker Basic Commands

- Execute the interactive terminal in a container.

  ```text
  docker exec -it {container-id} bash
  ```

  - Reference:

    - <https://stackoverflow.com/questions/20932357/docker-enter-running-container-with-new-tty>

    - <https://docs.docker.com/engine/reference/commandline/exec/>

- Show all the registered container.

  ```text
  docker ps --all
  ```

- Remove a specific container.

  ```text
  docker rm {container-id}
  ```

- Show all the registered images.

  ```text
  docker images
  ```

- Build an image.

  ```text
  docker build --tag={image-name:tag-version} {docker-file-path}
  ```

- Remove a specific image.

  ```text
  docker rmi {image-id|image-name}
    -f Option force removal of the docker image.
  ```

- Run a container.

  ```text
  docker run -it -p {host-port:container-port} {docker-image}
  ```

  - Reference:
  
    - <https://docs.docker.com/engine/reference/commandline/run/#add-host-device-to-container-device>

- Stop all the registered containers.

  ```text
  docker stop $(docker ps -a -q)
  ```

- Remove all the registered containers.

  ```text
  docker rm $(docker ps -a -q)
  ```

- Show the docker events.

  ```text
  docker events
  ```

  - Reference:
  
    - <https://docs.docker.com/engine/reference/commandline/events/#format-the-output>

- Show the docker logs.

  ```text
  docker logs
  ```
