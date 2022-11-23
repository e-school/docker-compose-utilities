# Kafka Docker Compose Utilities

This directory contains the docker compose utilities for Apache Kafka for single and cluster environment.

## Single Zookeeper / Single Kafka
This configuration fits most development requirements.

- Zookeeper will be available at $DOCKER_HOST_IP:2181
- Kafka will be available at $DOCKER_HOST_IP:9092

Run with:
````
docker-compose -f zookeepeer-single-kafka-single.yml up
docker-compose -f zookeepeer-single-kafka-single.yml down
````

## Single Zookeeper / Multiple Kafka
If you want to have three brokers and experiment with kafka replication / fault-tolerance.

- Zookeeper will be available at $DOCKER_HOST_IP:2181
- Kafka will be available at $DOCKER_HOST_IP:9092,$DOCKER_HOST_IP:9093,$DOCKER_HOST_IP:9094

Run with:
````
docker-compose -f zookeepeer-single-kafka-multiple.yml up
docker-compose -f zookeepeer-single-kafka-multiple.yml down
````

## Multiple Zookeeper / Single Kafka
If you want to have three zookeeper nodes and experiment with zookeeper fault-tolerance.

- Zookeepers will be available at $DOCKER_HOST_IP:2181,$DOCKER_HOST_IP:2182,$DOCKER_HOST_IP:2183
- Kafka will be available at $DOCKER_HOST_IP:9092

Run with:
````
docker-compose -f zookeepeer-multiple-kafka-single.yml up
docker-compose -f zookeepeer-multiple-kafka-single.yml down
````

## Multiple Zookeeper / Multiple Kafka
If you want to have three zookeeper nodes and three kafka brokers to experiment with production setup.

- Zookeepers will be available at $DOCKER_HOST_IP:2181,$DOCKER_HOST_IP:2182,$DOCKER_HOST_IP:2183
- Kafkas will be available at $DOCKER_HOST_IP:9092,$DOCKER_HOST_IP:9093,$DOCKER_HOST_IP:9094

Run with:
````
docker-compose -f zookeepeer-multiple-kafka-multiple.yml up
docker-compose -f zookeepeer-multiple-kafka-multiple.yml down
````
