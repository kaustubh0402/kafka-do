- Reassign partiotion with leader and replication change
- suppose we have want to add more partition, we can use reassign partition

```
use partition-assign.json file
/opt/kafka/bin $ cat /tmp/partition-assign.json
{
  "partitions": [
    {"topic": "test-topic", "partition": 0, "replicas": [3, 2]},
    {"topic": "test-topic", "partition": 1, "replicas": [2, 3]},
    {"topic": "test-topic", "partition": 2, "replicas": [3, 2]}
  ],
  "version": 1
}

or used kafka recommendations from following command
./kafka-reassign-partitions.sh --topics-to-move-json-file /tmp/topics.json --generate --broker-list "2,3" --bootstrap-server kafka-broker-1:9094 

/opt/kafka/bin $
/opt/kafka/bin $ cat /tmp/topics.json
{
  "topics": [
    {"topic": "test-topic"}
  ],
  "version":1
}
```


- Actual assignment command

```
 ./kafka-reassign-partitions.sh  --reassignment-json-file /tmp/partition-assign.json --execute --bootstrap-server kafka-broker-1:9094
```


- Test progress of reassignment of topics

```
 ./kafka-reassign-partitions.sh  --reassignment-json-file /tmp/partition-assign.json --verify --bootstrap-server kafka-broker-1:9094
```

- Describe kafka topics

```
 ./kafka-topics.sh --describe --topic test-topic --bootstrap-server kafka-broker-1:9094
```
