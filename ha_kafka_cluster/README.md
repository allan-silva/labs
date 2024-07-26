## Zookeeper test

```
vagrant ssh zookeeper1

$ cd /opt/zookeeper/

# local connect
bin/zkCli.sh -client-configuration conf/zoo.conf

```

## Zoo cli commands

### List nodes in cluster

```
[zk: localhost:2181(CONNECTED) 2] config 

```

Expected output:

```
server.1=192.168.60.10:2888:3888:participant
server.2=192.168.61.11:2888:3888:participant
server.3=192.168.62.12:2888:3888:participant
version=0
```

### Connect to remote node
```
[zk: localhost:2181(CONNECTED) 5] connect 192.168.62.12:2181
```

Expected output:

```
...
[zk: 192.168.62.12:2181(CONNECTED) 2]

```

## Kafka test

```
vagrant ssh kafka1

$ cd /opt/kafka/

```

### Binaries commands

### Describe cluster brokers version info
```
bin/kafka-broker-api-versions.sh --bootstrap-server localhost:9092
```

Expected output:

```
192.168.62.22:9092 (id: 2 rack: zone-62) -> (
        Produce(0): 0 to 9 [usable: 9],
        ...
)
192.168.61.21:9092 (id: 1 rack: zone-61) -> (
        Produce(0): 0 to 9 [usable: 9],
        ...
)
192.168.60.20:9092 (id: 0 rack: zone-60) -> (
        Produce(0): 0 to 9 [usable: 9],
        ...
)
```
