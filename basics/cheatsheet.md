# Kafka CLI One-Page Cheat Sheet

## 1. Start / Stop Services

### Start ZooKeeper
Starts the ZooKeeper service required by Kafka (legacy setup).

```
bin/zookeeper-server-start.sh config/zookeeper.properties
```

### Start Kafka Broker
Starts the Kafka server using broker configuration.

```
bin/kafka-server-start.sh config/server.properties
```

### Stop Kafka Broker
Gracefully stops the Kafka server.
```
bin/kafka-server-stop.sh
```
### Stop ZooKeeper
Stops the ZooKeeper service.
```
bin/zookeeper-server-stop.sh
```

## 2. Topic Management

### List All Topics
Displays all topics available in the Kafka cluster.
```
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```
### Create Topic (Default Settings)
Creates a topic with default partitions and replication factor.
```
bin/kafka-topics.sh --bootstrap-server localhost:9092 --topic phishing-sites --create
```
### Create Topic (Custom Settings)
Creates a topic with 5 partitions and replication factor of 3.
```
bin/kafka-topics.sh --bootstrap-server localhost:9092
--topic phishing-sites
--create
--replication-factor 3
--partitions 5
```
### Describe Topic
Shows partition count, leaders, replicas, and ISR details.
```
bin/kafka-topics.sh --bootstrap-server localhost:9092
--topic known-infections --describe
```
### Delete Topic
Deletes the specified topic (if deletion is enabled).
```
bin/kafka-topics.sh --bootstrap-server localhost:9092
--topic hishing-sites --delete
```
## 3. Producers

### Console Producer (Interactive)
Allows manual message entry to a topic.
```
bin/kafka-console-producer.sh --bootstrap-server localhost:9092
--topic phishing-sites
```
### Send a Single Message
Sends one message using standard input.
```
echo "This is a test message" |
bin/kafka-console-producer.sh --bootstrap-server localhost:9092
--topic phishing-sites
```
## 4. Consumers

### Consume From Beginning
Reads all messages from the earliest offset.
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092
--topic phishing-sites --from-beginning
```
### Consume Limited Messages
Reads only the first 2 messages and stops.
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092
--topic phishing-sites --from-beginning --max-messages 2
```
## 5. Monitoring & Troubleshooting

### Check Kafka Processes
Verifies Kafka-related processes are running.
```
ps ax | grep kafka
```
### Check Kafka Port
Confirms Kafka is listening on port 9092.
```
netstat -tlnp | grep 9092
```
## Quick Memory Notes
- Producer → sends data  
- Consumer → reads data  
- Topics → message categories  
- Partitions → parallelism  
- Replication → fault tolerance  
- Port 9092 → Kafka broker  
- ZooKeeper → coordination (legacy Kafka)