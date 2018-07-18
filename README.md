# Simple Kafka Container with embedded ZooKeeper

At the moment GitLab CI does not easily support interconnecting services (see
[#15220](https://gitlab.com/gitlab-org/gitlab-ce/issues/15220)). This container
runs ZooKeeper as daemon and Kafka as foreground process, so it can be used
out-of-the-box for CI testing.

It follows [Apache Kafka Quickstart](https://kafka.apache.org/quickstart),
usings the CLI tools shipped with the binary release to start a ZooKeeper daemon
and the Kafka server.

## Env Options

Optionally use specific broker id, `docker run --rm -it --env=BROKER_ID=1 martinnowak/kafka`.
```
# generate unique id by default
ENV BROKER_ID=-1
```

## Volume

Optionally mount persistent volume, `docker run --rm -it --volume=/tmp/host/kafka:/var/lib/kafka martinnowak/kafka`.
```
VOLUME /var/lib/kafka
```

## Ports

Optionally publish ports on host, `docker run --rm -it --publish=2181:2181 --publish=9092:9092 martinnowak/kafka`.
```
EXPOSE 2181/tcp 9092/tcp
```

## Build Options

Optionally build with a different version, `docker build --build-arg=KAFKA_VERSION=0.11.0.2 .`.
```
ARG KAFKA_VERSION=1.1.0
ARG SCALA_VERSION=2.11
```

