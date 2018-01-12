# Docker Steps To Start

#### DOCKER BUILD IMAGE
```docker build --tag={php5/apache:latest} {/path}```

#### CREATE NETWORK BRIDGE
```
    docker network create --driver={bridge} --subnet={192.168.116.0/16} docker-bridge-local
```

#### RUN MYSQL SERVER USING BRIDGE 
```
    docker run --name={mysql-server} --net={docker-bridge-local} --ip={192.168.116.2} -v {/var/lib/docker-mysql-5.6/:/var/lib/mysql} -e MYSQL_ROOT_PASSWORD={password} -d -p {3306:3306} {mysql:5.6}
```

#### RUN PHPMYADMIN USING BRIDGE
```
    docker run -d --name={phpmyadmin-dev} --net={docker-bridge-local} --ip={192.168.116.3} -p {8800:80} --link={mysql-server:db} {phpmyadmin/phpmyadmin:latest}
```

#### RUN THE WEBSERVER APACHE FOR MY CASE USING BRIDGE
```
    docker run --name={} --net={docker-bridge-local} --ip={192.168.x.x} -it -v {/var/www/site/source/path:/var/www/site/} -p {0000:80} --link={mysql-server} {repository:tag} bash
```  

```
Sample actual usage:

docker run --name={project-nestea-beach-2017} --net={docker-bridge-local} --ip={192.168.116.100} -it -v {/var/www/site/drupal/nestea-beach-2017/:/var/www/site/} --link={mysql-server:db} {php5/apache:latest} bash
docker run --name={project-creamsilk-2017} --net={docker-bridge-local} --ip={192.168.116.101} -it -v {/var/www/site/wordpress/creamsilk-2017/:/var/www/site/} --link={mysql-server:db} {php5/apache:latest} bash
```    

#### BASH IN THE CONTAINER
```docker exec -it <container id> bash```

#### START THE SERVER AFTER BASH
```service apache2 start```