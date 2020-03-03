# TimescaleDB out of the box with docker-compose
Simply run timescaledb in a managed docker container with docker-compose.

## Setup

Configure your version of timescaledb and the underlying PostgreSQL version by adapting `image: timescale/timescaledb:1.6.0-pg10` to `image: timescale/timescaledb:<timescale_version>-pg<postgres_major_version>` in the docker-compose file. Available versions are specified at [dockerhub](https://hub.docker.com/r/timescale/timescaledb/). 

For example, you can run the latest release based on PostgreSQL 11 by specifying `image: timescale/timescaledb:latest-pg11`.

Start the container via `docker-compose up -d` from this directory and then connect to the psql cli and start by creating a first database.

```
docker exec -it timescale psql -h localhost -U postgres
psql ~~ CREATE DATABASE helloworld;
```

The `db_data` volume will be persisted in your local docker volume directory. For example, you can find your postgresql.conf file to adapt settings via:
```
vi /var/lib/docker/volumes/timescale_db_data/_data/postgresql.conf
```