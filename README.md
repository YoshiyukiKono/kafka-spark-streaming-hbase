# kafka &middot; spark streaming example

This is a simple example of the integration of Kafka, Spark Streaming, and HBase.

### Prerequisites

#### Development
Java 1.8 or newer version required because lambda expression used for few cases

- Java >= 1.8 (Oracle JDK has been tested)
- Maven >= 3

#### Real-time Data Source

- Kafka >= 0.10.1.0

#### Hadoop/Cloudera CDH Cluster

- Apache Spark >= 2.0.2
- HBase = 2.1.0-cdh6.3.2

### Compile

Use Maven as follows for creating jar files, after you clone this repository,

```bash
$ mvn clean package -DskipTests
```

### Configuration

Edit `config/common.conf`, and change <Your Kafka Server> to the IP address of your Kafka server (It must be a private IP if you use AWS).

```
producer {
  ...
  topic: "test-default"

  hosts: [
    "<Your Kafka Server>:9092"
  ]
}
```

### Usage

Start the Spark streaming service and it'll process events from Kafka topic to HBase,

```bash
spark-submit --master local[*]  --driver-java-options "-Dconfig=./config/common.conf -Dlog4j.configuration=file:log4j.xml" streaming/target/spark-streaming-0.1.jar
```



