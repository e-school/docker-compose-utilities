# elastic docker-compose utilities

This directory contains the docker compose utilities for elastic database single and cluster environment.

## Single  Environment
NOTE: This configuration fits most development requirements, not recommended for production usage. If you want to configure for clustered environment, repeat the same configuration with different cluster names. 

Run with:
````
docker-compose -f elastic-docker-compose.yml up ## To pull/start the docker image
docker-compose -f elastic-docker-compose.yml down ## To stop and remove the docker image
````

### Access Elasticsearch Data base using Kibana
- Kibana URL : http://localhost:5601/app/kibana (any free port cane be used, but define them in docker compose yml file)


### Access Kibana web interface
 - Access web url `http://localhost:5601/app/kibana` in browser. application looks like below.
![img.png](kibana.png)
