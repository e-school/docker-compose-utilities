# Redis Setup using docker compose
This is very simple way to setup redis-stack-server docker image using docker compose
## Create/save redis-docker-compose.yml file on your machine from the redis-docker-compose folder

### Parameters information
healthcheck: Defines a health check for the container. The healthcheck runs the specified command redis-cli

--raw incr ping to check if the Redis server is responding properly.

volumes: Creates a volume named redis_data. This volume is used to persist data, ensuring that even if the container is stopped or removed, the data stored by Redis remains accessible in subsequent container runs.

###Run the Redis stack
Save the docker-compose.yml file and run this in your terminal:
_docker compose up -d_

###Verify the Redis setup
Now, go ahead and open your favorite Redis client and connect to localhost:6379.