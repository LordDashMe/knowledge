# Docker Commands

#### Docker Container Run.
```docker exec -it [container-id] bash``` 

* https://stackoverflow.com/questions/20932357/docker-enter-running-container-with-new-tty
* https://docs.docker.com/engine/reference/commandline/exec/

#### Docker Show Container All.
```docker ps --all```

#### Docker Remove Container.
```docker rm <container id>```

#### Docker Images All.
```docker images```

#### Docker Build Image.    
```docker build --tag={} /path```

#### Docker Remove Image.    
```docker rmi {-f} - this will force delete the image```

#### Docker Run Mysql
```docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag```

* https://stackoverflow.com/questions/33299303/how-to-build-a-docker-container-with-a-running-mysql?noredirect=1

#### Docker Run
```docker run -i -t -p 8080:80 ubuntu:latest```

* https://docs.docker.com/engine/reference/commandline/run/#add-host-device-to-container-device

#### Docker Stop All Containers
```docker stop $(docker ps -a -q)```

#### Docker Remove All Containers
```docker rm $(docker ps -a -q)```
