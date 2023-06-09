# Mongodb docker-compose utilities

This directory contains the docker compose utilities for mongodb database single and cluster environment.

## Single Mongodb Environment with MongoExpress
NOTE: This configuration fits most development requirements, not recommended for production usage.

- mongodb tcp/ip connection available at $DOCKER_HOST_IP:27017
- mongo-express interface available at $DOCKER_HOST_IP:8081

Run with:
````
docker-compose -f mongodb-mongo-express-docker-compose.yml up ## To pull/start the docker image
docker-compose -f mongodb-mongo-express-docker-compose.yml down ## To stop and remove the docker image
````

### Access database using the TCP/IP
- Connection string : mongodb://root:example@mongo:27017/
  - Username: root
  - Password: example

### Access database on mongo-express web interface
 - Access web url `localhost:8082` in browser. application looks like below.
![img.png](mongo-express.png)
 - Provide below details:
   - Username: root
   - Password: example
 - Use the database interface as needed.

