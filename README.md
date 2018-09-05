# Simple Kafka Container with embedded ZooKeeper

Forked from and all due respect to https://github.com/MartinNowak/docker-kafka

Small, lightweight Kafka standup service for integration tests to be carried out on drone

It follows [Apache Kafka Quickstart](https://kafka.apache.org/quickstart),
usings the CLI tools shipped with the binary release to start a ZooKeeper daemon
and the Kafka server.


## Drone Usage

Create a mock kafka in your build steps for integration testing. 
```
--
services:
  image: quay.io/ukhomeofficedigital/kafkazoo
```

## Env Options

Optionally use specific broker id, `docker run --rm -it --env=BROKER_ID=1 quay.io/ukhomeofficedigital/kafkazoo`.
```
# generate unique id by default
ENV BROKER_ID=-1
```

## Volume

Optionally mount persistent volume, `docker run --rm -it --volume=/tmp/host/kafka:/var/lib/kafka quay.io/ukhomeofficedigital/kafkazoo`.
```
VOLUME /var/lib/kafka
```

## Ports

Optionally publish ports on host, `docker run --rm -it --publish=2181:2181 --publish=9092:9092 quay.io/ukhomeofficedigital/kafkazoo`.
```
EXPOSE 2181/tcp 9092/tcp
```

## Build Options

Optionally build with a different version, `docker build --build-arg=KAFKA_VERSION=0.11.0.2 .`.
```
ARG KAFKA_VERSION=1.0.0
ARG SCALA_VERSION=2.11
```
