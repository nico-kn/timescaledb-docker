# timescaledb-docker
Simply run timescaledb in a managed docker container with docker-compose.

Start the container via `docker-compose up -d` from this directory and then connect to the psql cli and start by creating a first database.

```
docker exec -it timescale psql -h localhost -U postgres
psql ~~ CREATE DATABASE helloworld;
```

The `db_data` volume will be persisted in your local docker volume directory. For example, you can find your postgresql.conf file to adapt settings via:
```
vi /var/lib/docker/volumes/timescale_db_data/_data/postgresql.conf
```