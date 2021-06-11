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

Finally, cloudera-quickstart docker version (used on course as VM).

```bash
docker pull cloudera/quickstart
docker run --name cloudera --network=cloudera-postgres --hostname=quickstart.cloudera --privileged=true -t -d -p 8888:8888 -p 80:80 -p 7180:7180 -v C:\Users\msartor\Documents\Morgana\Code\Github-Projects\data-engineer-formation\volumes\cloudera:/src cloudera/quickstart /usr/bin/docker-quickstart
```
