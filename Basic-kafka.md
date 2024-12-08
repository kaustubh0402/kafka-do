# Kafka-Docker-Setup


 - Clone this repository

 - Move inside the cloned directory and execute the following command (Make sure docker is running)

```
docker compose up -d
```

 - Now once the container is up, use the following command to enter the kafka shell running inside the container

```
 docker exec -it -w /opt/kafka/bin broker sh
```

- To Add a topic in Kafka,

```
./kafka-topics.sh --create --topic sample-topic --bootstrap-server broker:29092
```

- To start consumer on a topic,

```
./kafka-console-consumer.sh --topic sample-topic --from-beginning --bootstrap-server broker:29092
```


- To produce the data in the topic,

```
./kafka-console-producer.sh --topic sample-topic --bootstrap-server broker:29092
```
