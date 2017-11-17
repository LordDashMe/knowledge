
# DOCKER BASIC COMMANDS #

* Docker Container Run.

    ```docker exec -it [container-id] bash``` 

    - https://stackoverflow.com/questions/20932357/docker-enter-running-container-with-new-tty
    - https://docs.docker.com/engine/reference/commandline/exec/

* Docker Show Container All.
    
    ```docker ps --all```

* Docker Remove Container.
    
    ```docker rm <container id>```

* Docker Images All.
    
    ```docker images```

* Docker Build Image.
    
    ```docker build --tag={} /path```

* Docker Remove Image.
    
    ```docker rmi {-f} - this will force delete the image```

* Docker Run Mysql

    ```docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag```

    - https://stackoverflow.com/questions/33299303/how-to-build-a-docker-container-with-a-running-mysql?noredirect=1

* Docker Run

    ```docker run -i -t -p 8080:80 ubuntu:latest```

    - https://docs.docker.com/engine/reference/commandline/run/#add-host-device-to-container-device

* Docker Stop All Containers

    ```docker stop $(docker ps -a -q)```

* Docker Remove All Containers

    ```docker rm $(docker ps -a -q)```

# DOCKER COMMON STEPS TO START #

* DOCKER BUILD IMAGE
    
    ```docker build --tag={php5/apache:latest} {/path}```

* CREATE NETWORK BRIDGE
    
```
    docker network create --driver={bridge} --subnet={192.168.116.0/16} docker-bridge-local
```

* RUN MYSQL SERVER USING BRIDGE
    
```
    docker run --name={mysql-server} --net={docker-bridge-local} --ip={192.168.116.2} -v {/var/lib/docker-mysql-5.6/:/var/lib/mysql} -e MYSQL_ROOT_PASSWORD={password} -d -p {3306:3306} {mysql:5.6}
```

* RUN PHPMYADMIN USING BRIDGE
    
```
    docker run -d --name={phpmyadmin-dev} --net={docker-bridge-local} --ip={192.168.116.3} -p {8800:80} --link={mysql-server:db} {phpmyadmin/phpmyadmin:latest}
```

* RUN THE WEBSERVER APACHE FOR MY CASE USING BRIDGE
    
```
    docker run --name={} --net={docker-bridge-local} --ip={192.168.x.x} -it -v {/var/www/site/source/path:/var/www/site/} -p {0000:80} --link={mysql-server} {repository:tag} bash
```  

```
    Ex:
    
        docker run --name={project-nestea-beach-2017} --net={docker-bridge-local} --ip={192.168.116.100} -it -v {/var/www/site/drupal/nestea-beach-2017/:/var/www/site/} --link={mysql-server:db} {php5/apache:latest} bash

        docker run --name={project-creamsilk-2017} --net={docker-bridge-local} --ip={192.168.116.101} -it -v {/var/www/site/wordpress/creamsilk-2017/:/var/www/site/} --link={mysql-server:db} {php5/apache:latest} bash
```    

* BASH IN THE CONTAINER

    ```docker exec -it <container id> bash```

* START THE SERVER AFTER BASH

    ```service apache2 start```
