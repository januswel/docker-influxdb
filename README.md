InfluxDB container
==================

For default use, docker-compose.yml is like below.

```docker-compose.yml
influxdb:
  image: januswel/influxdb
  container_name: influxdb
  volumes:
    - ~/docker/influxdb/influxdb.conf:/etc/influxdb/influxdb.conf
    - /var/lib/influxdb/data
  ports:
    - 8083:8083
    - 8086:8086
    - 8088:8088
```

To get influxdb.conf, run below commands.

```sh
docker run -d --name influxdb januswel/influxdb
docker cp influxdb:/etc/influxdb/influxdb.conf .
docker rm -f influxdb
```

Start container.

```sh
docker-compose up -d
```

And then, create your database and use it.
Note that installing "influx" command to your local machine is needed.
<machine-ip> is "localhost" with Linux machine, or ip address got by "docker-machine ip <machine-name>" with docker-machine command.

```sh
influx --host <machine-ip> --port 8086
```

```influxql
CREATE DATABASE mydb
USE mydb
```
