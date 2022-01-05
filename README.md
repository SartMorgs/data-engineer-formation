# data-engineer-formation
all of course https://www.udemy.com/course/engenheiro-de-dados/


# prepare environment
First of all we will need a relational database for our case of study

```bash
docker pull postgres
docker run --name postgres-cloudera --network=cloudera-postgres -e POSTGRES_USER=msartor -e POSTGRES_PASSWORD=@Kisuco5004 -e POSTGRES_DB=jjbike -v $(pwd):/var/lib/postgresql/data -p 5432:5432 -d postgres
```

And a database administrator system for use with postgres.

``` bash
docker pull dpage/pgadmin4
docker run --name pgadmin4 --network=cloudera-postgres -e PGADMIN_DEFAULT_EMAIL=msartor@weg.net -e PGADMIN_DEFAULT_PASSWORD=@Kisuco5004 -p 15432:80 -d dpage/pgadmin4
```

Also is necessaring a mongodb

``` bash
docker pull mongo
docker run --name mongodb-cloudera --network=mongo-network -e MONGO_INITDB_ROOT_USERNAME=msartor -e MONGO_INITDB_ROOT_PASSWORD=@Kisuco5004 -v $(pwd):/data/db -p 27017:27017 -d mongo
```

And a database administrator for this.
``` bash
docker pull mongo-express
docker run --name mongo-express -e ME_CONFIG_BASICAUTH_USERNAME=msartor -e ME_CONFIG_BASICAUTH_PASSWORD=@Kisuco5004 -e ME_CONFIG_MONGODB_PORT=27017 -e ME_CONFIG_MONGODB_ADMINUSERNAME=msartor -e ME_CONFIG_MONGODB_ADMINPASSWORD=@Kisuco5004 -p 8081:8081 -d mongo-express
```

Finally, cloudera-quickstart docker version (used on course as VM).

```bash
docker pull cloudera/quickstart
docker run --name cloudera --network=cloudera-postgres --hostname=quickstart.cloudera --privileged=true -t -d -p 8888:8888 -p 80:80 -p 7180:7180 -v C:\Users\msartor\Documents\Morgana\Code\Github-Projects\data-engineer-formation\volumes\cloudera:/src cloudera/quickstart /usr/bin/docker-quickstart
```
