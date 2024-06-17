# Timescale database docker-compose utilities

## TimeScaleDB:
Timescale is a cloud-based PostgreSQL platform for resource-intensive workloads. It is a time-series database that is built on top of PostgreSQL. It is designed to scale and handle high-performance queries and real-time data. It is optimized for fast ingest and complex queries.
TimescaleDB instance optimized for your time-series and analytics workloads. Get automated dynamic data partitioning, hybrid row-columnar storage, advanced compression techniques, incremental up-to-date materializations, and specialized analysis functions as well as cloud-only features like transparent tiering and low-cost object storage
## Time Series Data
Time-series data represents how a system, process, or behavior changes over time. For example, if you are taking measurements from a temperature gauge every five minutes, you are collecting time-series data. Another common example is stock price changes, or even the battery life of your smart phone. As these measurements change over time, each data point is recorded alongside its timestamp, allowing it to be measured, analyzed, and visualized.

Time-series data can be collected very frequently, such as financial data, or infrequently, such as weather or system measurements. It can also be collected regularly, such as every millisecond or every hour, or irregularly, such as only when a change occurs.

## How to Use this docker file ?
Simply run following commands to start and stop docker imageRun with:
````
docker-compose -f timescale-db-docker-compose.yml up ## To pull/start the docker image
docker-compose -f timescale-db-docker-compose.yml down ## To stop and remove the docker image
````

### Access Timescale using the TCP/IP
Timescale has support for wide variety of programming languages such as Node, Java PythonRuby Golang etc.., below page describes the client libraries
https://docs.timescale.com/quick-start/latest/

### replace "path-to-db-data-directory" with your local path where you want to store the data
## Note: This configuration NOT recommended for production usage, it's only for development and get yourself familiarised with Timescale DB
