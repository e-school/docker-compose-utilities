# Cassandra database docker-compose utilities

This directory contains the docker compose utilities for creating a Cassandra multinode database cluster.

## MultiNode Cluster Environment

This project is based on [official docker image](https://hub.docker.com/_/cassandra/) maintained by [Docker Hub](https://docs.docker.com/docker-hub/official_images/) to start a simple multi-node cluster for local development.

> NOTE: This configuration fits most of development environment requirements and is not recommended for production usage.

### Configuration

- This set up will start up a 3-node Cassandra database cluster. You can configure the number of containers in [compose] specification(./cassandra-multi-node-docker-compose.yml/cassandra-multi-node-docker-compose.yml).
- `data` is stored in [docker volumes](https://docs.docker.com/storage/volumes/#use-a-volume-with-docker-compose) named `cassandra-volume-*` on the host host filesystem which is managed by Docker at `/var/lib/docker/volumes/`.
- The cluster can be accessed on [client port address](http://localhost:9042).

### Quick start

To start up a local cluster on the machine:

```sh
cd ./cassandra-docker-compose

## Review the compose config (Optional)
docker compose -f cassandra-docker-compose.yml config

## Start cluster
docker compose -f cassandra-docker-compose.yml up

## Or alternatively run in background and check status
docker compose -f cassandra-docker-compose.yml up -d
docker compose -f cassandra-docker-compose.yml ps
```

### Usage

Once cluster is up, you can create keyspaces as you need. You can use [`nodetool`](https://cassandra.apache.org/doc/stable/cassandra/tools/nodetool/nodetool.html) to verify the status and [`cqlsh`](https://cassandra.apache.org/doc/stable/cassandra/tools/cqlsh.html) to create keyspaces and tables.

More information is available [here](https://cassandra.apache.org/_/quickstart.html).

```sh
## Outputs cluster and gossip status
docker compose -f cassandra-docker-compose.yml \
  exec cassandra-1 \
  nodetool status

docker compose -f cassandra-docker-compose.yml \
  exec cassandra-1 \
  nodetool statusgossip

## Run script in cqlsh to seed sample data
cat <<EOF | docker compose -f cassandra-docker-compose.yml exec \
  -T cassandra-1 \
  cqlsh

-- Create a keyspace
CREATE KEYSPACE IF NOT EXISTS my_store WITH REPLICATION = {
  'class' : 'SimpleStrategy',
  'replication_factor' : '1'
};

-- Create a table
CREATE TABLE IF NOT EXISTS my_store.shopping_cart (
  userid text PRIMARY KEY,
  item_count int,
  last_update_timestamp timestamp
);

-- Insert data
INSERT INTO my_store.shopping_cart (userid, item_count, last_update_timestamp)
VALUES ('1234', 2, toTimeStamp(now()));

INSERT INTO my_store.shopping_cart (userid, item_count, last_update_timestamp)
VALUES ('1235', 1, toTimeStamp(now()));  

-- Terminate the shell
EXIT;

EOF

## Run script in cqlsh to query sample data
cat <<EOF | docker compose -f cassandra-docker-compose.yml \
  exec -T cassandra-1 \
  cqlsh

-- Query data
SELECT * FROM my_store.shopping_cart;

-- Terminate the shell
EXIT;

EOF
```

### Restart the cluster

To restart the running local cluster on the machine:

```sh
docker compose -f cassandra-docker-compose.yml restart
```

### Stop the cluster

To stop the running local cluster on the machine:

```sh
docker compose -f cassandra-docker-compose.yml down

## Or alternatively stop if you have run in detached mode
docker compose -f cassandra-docker-compose.yml stop
```

### Remove docker volumes

The volumes created are persisted on disk and survives cluster restarts. To remove the docker volumes created:

```sh
docker volume rm cassandra-volume-1 \
  cassandra-volume-2 \
  cassandra-volume-3
```
