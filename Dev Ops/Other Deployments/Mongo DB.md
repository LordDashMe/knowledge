
### LINK MONGODB TO CONTAINER: ###

#### STEP 1: ####
```
docker run --name=mongo-server --net=docker-bridge-local --ip=192.168.116.4 -v /var/lib/docker-mongo-3.4.10/:/var/lib/mongo -p 58808:27017 -d mongo:3.4.10
```

#### STEP 2: ####
```
docker exec -it mongo-server mongo --port 27017
```

#### STEP 3: ####
```
db.createUser(
  {
    user: "admin",
    pwd: "password",
    roles: [ { role: "readWriteAnyDatabase", db: "admin"} ]
  }
)
```

#### STEP 4: ####
```
docker exec -it mongo-server mongod --auth --port 27017
```

#### STEP 5: ####
```
docker exec -it mongo-server mongo --port 27017 -u "admin" -p "password" --authenticationDatabase "admin"
```

#### STEP 6: ####
```
db.createUser(
  {
    user: "admin",
    pwd: "password",
    roles: [ { role: "readWrite", db: "test-mongo" } ]
  }
)
```

#### STEP 7: ####
```
docker run --name=project-test-mongo --net=docker-bridge-local --ip=192.168.116.108 -it -v /var/www/site/others/test-mongo/:/var/www/site/ -p 8810:80 --link=mongo-server php5.6/apache-mongo:stable bash
```

### HOW TO USE MONGO DB IN PHP 5.6: ###
https://www.tutorialspoint.com/mongodb/mongodb_php.htm