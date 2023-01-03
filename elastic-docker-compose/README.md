# elastic docker-compose utilities

This directory contains the docker compose utilities for elastic database single and cluster environment.

## Single  Environment
NOTE: This configuration fits most development requirements, not recommended for production usage.

- postgres tcp/ip connection available at $DOCKER_HOST_IP:5432
- postgres ui interface available at at $DOCKER_HOST_IP:8080

Run with:
````
docker-compose -f elastic-docker-compose.yml up ## To pull/start the docker image
docker-compose -f elastic-docker-compose.yml down ## To stop and remove the docker image
````

### Access database using the TCP/IP
- Connection string : jdbc:postgresql://localhost:5432/postgres
  - Username: postgres
  - Password: postgres

### Access database on web interface
 - Access web url `localhost:8080` in browser. application looks like below.
![img.png](img.png)
 - Provide below details:
   - System: PostgreSQL
   - Server: postgres
   - Username: postgres
   - Password: postgres
 - Create database, tables as needed.