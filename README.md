# data-engineer-formation
all of course https://www.udemy.com/course/engenheiro-de-dados/


# prepare environment
First of all we will need a relational database for our case of study

```bash
docker pull postgres
docker run --name postgres-cloudera --network=cloudera-postgres -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=admin -e POSTGRES_DB=jjbike -v $(pwd):/var/lib/postgresql/data -p 5432:5432 -d postgres
```

And a database administrator system for use with postgres.

``` bash
docker pull dpage/pgadmin4
docker run --name pgadmin4 --network=cloudera-postgres -e PGADMIN_DEFAULT_EMAIL=admin@example.com -e PGADMIN_DEFAULT_PASSWORD=admin -p 15432:80 -d dpage/pgadmin4
```

Also is necessaring a mongodb

``` bash
docker pull mongo
docker run --name mongodb-cloudera --network=mongo-network -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=admin -v $(pwd):/data/db -p 27017:27017 -d mongo
```

And a database administrator for this.
``` bash
docker pull mongo-express
docker run --network=mongo-network --name mongo-express -e ME_CONFIG_BASICAUTH_USERNAME="admin" -e ME_CONFIG_BASICAUTH_PASSWORD="admin" -e ME_CONFIG_MONGODB_SERVER="mongodb-cloudera" -e ME_CONFIG_MONGODB_PORT=27017 -e ME_CONFIG_MONGODB_ADMINUSERNAME="admin" -e ME_CONFIG_MONGODB_ADMINPASSWORD="admin" -p 8081:8081 -d mongo-express
```

Finally, cloudera-quickstart docker version (used on course as VM).

```bash
docker pull cloudera/quickstart
docker run --name cloudera --network=cloudera-postgres --hostname=quickstart.cloudera --privileged=true -t -d -p 8888:8888 -p 80:80 -p 7180:7180 -v $(pwd):/src cloudera/quickstart /usr/bin/docker-quickstart
```
