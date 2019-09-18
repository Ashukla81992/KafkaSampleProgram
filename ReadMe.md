###### Topics
Kafka is run as a cluster in one or more servers and the cluster stores/retrieves the records in a feed/category called Topics. Each record in the topic is stored with a key, value, and timestamp.
The topics can have zero, one, or multiple consumers, who will subscribe to the data written to that topic. In Kafka terms, topics are always part of a multi-subscriber feed.

###### Partitions
The Kafka cluster uses a partitioned log for each topic.

The partition maintains the order in which data was inserted and once the record is 
published to the topic, it remains there depending on the retention period (which is configurable).
The records are always appended at the end of the partitions. It maintains a flag called 'offsets,'
 which uniquely identifies each record within the partition.
The offset is controlled by the consuming applications. 
Using offset, consumers might backtrace to older offsets and reprocess the records if needed.

###### Producers
The stream of records, i.e. data, is published to the topics by the producers. 
They can also assign the partition when it is publishing data to the topic. 
The producer can send data in a round robin way or it can implement a priority 
  system based on sending records to certain partitions based on the priority of the record.

###### Consumers
Consumers consume the records from the topic. They are based on the concept of a consumer-group, where some of the consumers are assigned in the group. The record which is published to the topic is only delivered to one instance of the consumer from one consumer-group. Kafka internally uses a mechanism of consuming records inside the consumer-group. Each instance of the consumer will get hold of the particular partition log, such that within a consumer-group, the records can be processed parallelly by each consumer



Location of Kafka in laptop : /Users/abshukla/Needed_Software/kafka_2.12-2.3.0/


To run Kafka Zoo Keeper: bin/zookeeper-server-start.sh config/zookeeper.properties


To run Kafka server: bin/kafka-server-start.sh config/server.properties


To Compile and build:- mvn clean package / mvn clean install
To run the code:-  java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,suspend=n -jar target/demo-0.0.1-SNAPSHOT.jar 


TO CALL THE API:- 
curl -X POST \
  'http://localhost:9000/kafka/publish?message=babaShakalaka' \
  -H 'cache-control: no-cache'\