# Linux Apache MySQL PHP Stack

Example steps implementing LAMP stack using docker.

- Build a Docker Image.

  ```text
  docker build --tag={php5/apache:latest} {docker-file-path}
  ```

- Create a Network Bridge.

  ```text
  docker network create --driver=bridge --subnet={192.168.116.0/16} {docker-bridge-local}
  ```

- Run a MySQL Server with Network Bridge.

  ```text
  docker run --name={mysql-server} --net={docker-bridge-local} --ip={192.168.116.2} -v {/var/lib/docker-mysql-5.6/:/var/lib/mysql} -e MYSQL_ROOT_PASSWORD={password} -d -p {3306:3306} {mysql:5.6}
  ```

- Run a PHPMyAdmin with Network Bridge.

  ```text
  docker run -d --name={phpmyadmin-dev} --net={docker-bridge-local} --ip={192.168.116.3} -p {8800:80} --link={mysql-server:db} {phpmyadmin/phpmyadmin:latest}
  ```

- Run a Docker Image PHP5 Apache to generate Container with Network Bridge.

  ```text
  docker run --name={docker-container-name} --net={docker-bridge-local} --ip={192.168.x.x} -it -v {/var/www/site/source/path:/var/www/site/} -p {0000:80} --link={mysql-server} {php5/apache:latest]} bash
  ```  

  ```text
  docker run --name={project-test-2017} --net={docker-bridge-local} --ip={192.168.116.100} -it -v {/var/www/site/drupal/test-2017/:/var/www/site/} --link={mysql-server:db} {php5/apache:latest]} bash
  ```

- Run Interactive Terminal in the Docker Container.

  ```text
  docker exec -it {container-id|container-name} bash
  ```

- Run command inside of the Docker Container.

  ```text
  docker exec service apache2 start {container-id|container-name}
  ```
