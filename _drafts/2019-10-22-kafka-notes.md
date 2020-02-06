---
layout: post
title:  "Algorithms: Dynamic Programming"
categories: algorithms dynamic-programming
---

## Kafka CLI commands

### Topics

*Create a topic*
`kafka-topics --zookeeper 127.0.0.1:2181 --topic topic_name --create
--partitions 3 --replication-factor 1`

*list topics*
`kafka-topics --zookeeper 127.0.0.1:2181 --list`

*topic info*
`kafka-topics --zookeeper 127.0.0.1:2181 --topic topic_name --describe`

*topic deletion*
`kafka-topics --zookeeper 127.0.0.1:2181 --topic topic_name --delete`

### Producers

*Basic producer console mode*
`kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic`

*With more options*
`kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic
--producer-property acks=all`

### Consumers
*basic consumer*
`kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic`

*Include history*
`kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic
--from-beginning`

## Security in Kafka
 * Currently, any client can access your kafka cluster (authentication)
 * The clients can publish / consume any topic data (authorization)
 * All data being sent is fully visible on the network (encryption)

 * Someone could intercept data being sent
 * someone could publish bad data / steal data
 * someone could delete topics
