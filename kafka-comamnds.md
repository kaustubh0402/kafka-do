# Kafka-Docker-Setup

- To Add a topic in Kafka on multple broker with partition 3 and replication 2
- Note that : Replication Factor > Number of Brokers: This will fail if the replication factor exceeds the number of brokers in your cluster.     Ensure replication-factor <= number of brokers.

```
./kafka-topics.sh --create --topic test-topic --partitions 3 --replication-factor 2 --bootstrap-server kafka-broker-1:9094
```

- To list kafka topics

```
./kafka-topics.sh --list --bootstrap-server kafka-broker-1:9094
```

- To describe kafka topics

```
./kafka-topics.sh --list --bootstrap-server kafka-broker-1:9094
```

- Important kafka configuration information

```
meta.properties = contains cluster id and node id ( path (KAFKA_LOG_DIRS): generally inside logs directory (/tmp/kafka/logs/meta.properties))
broker related information: ./kafka-broker-api-versions.sh --bootstrap-server kafka-broker-1:9094
In docker : KAFKA_CONTROLLER_QUORUM_VOTERS : provide all controller nodes for forming quorum
In docker : KAFKA_PROCESS_ROLES : controller or broker or both
In docker : KAFKA_LISTENERS : <KAFKA_PROCESS_ROLES>://<node-name>:<port>
In docker : add depends_on controller for all brokers
In docker : mentioned volume path ( If using wsl provide proper path (/home/spirit/kafka/<server>)) provide proper perm if docker not starting
```

-

```

```

-

```

```

- To start consumer on a topic,

```
./kafka-console-consumer.sh --topic sample-topic --from-beginning --bootstrap-server broker:29092
```


- To produce the data in the topic,

```
./kafka-console-producer.sh --topic sample-topic --bootstrap-server broker:29092
```