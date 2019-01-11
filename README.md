# Full-stack Docker compose with Kafka, Zookeeper, Schema-registry and UI's
Local full-stack docker-compose where you have Zookeeper, Kafka, Schema-registry (and UI) and Topics (UI). This solves the networking hurdles that comes with Docker/docker-compose and should work across all platforms

## Setup
Create the following directories:
```mkdir -p zookeeper/data zookeeper/datalog kafka/data```

## Run it
Via ```export DOCKER_HOST_IP=127.0.0.1; docker-compose up```

## UI's:
The following UI's are part of this:
* Schema registry UI: http://localhost:8001/
* Topics UI: http://localhost:8000/
* Zoonavigator: http://localhost:8004/ (connect via: zookeeper:2181)

