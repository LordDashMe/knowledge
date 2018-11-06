# Cleanup

- Once in a while, you may need to cleanup unused containers, volumes, images and networks.

- Make sure to double check and backup the data that may depend on docker before committing any actions.

- Remove unused volumes.

  ```text
  docker volume rm $(docker volume ls -qf dangling=true)
  ```

  ```text
  docker volume ls -qf dangling=true | xargs -r docker volume rm
  ```

  - Reference:

    - <https://github.com/chadoe/docker-cleanup-volumes>

- Remove networks.

  - To show all the existing docker networks.

    ```text
    docker network ls
    docker network ls | grep "bridge"
    ```

  - To remove all the unused bridge networks.

    ```text
    docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')
    ```

- Remove docker images.

  - To show all existing docker images or with none name status.
  
    ```text
    docker images
    docker images | grep "none"
    ```
  
  - To remove all the unused docker images.

    ```text
    docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
    ```

    ```text
    docker rmi $(docker images | grep "none" | awk '/ / { print $3 }')
    ```

  - Reference:

    - <http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images>

- Remove docker containers.

  - To show all the existing docker containers.
  
    ```text
    docker ps
    docker ps -a
    ```
  
  - To remove all the unused docker images.

    ```text
    docker rm $(docker ps -qa --no-trunc --filter "status=exited")
    ```

  - Resize disk space for docker vm.

  ```text
  docker-machine create --driver virtualbox --virtualbox-disk-size "40000" default
  ```

  - Reference:
  
    - <http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images>  
