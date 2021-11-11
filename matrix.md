
## Unconditionals

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Community           | Apache             | RedHat (?)         | Linux Foundation   | Apache             | Apache             
License             | ALv2               | MPL                | ALv2               | ALv2               | ALv2               
Community Support   | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb::bulb:       | :bulb::bulb::bulb: | :bulb::bulb:       
Commercial Support  | :heavy_check_mark: Confluent | :heavy_check_mark: VMware | :heavy_check_mark: Synadia Communic. | StreamNative.io | :heavy_check_mark: RedHat, ++ 
Operating System    | All JVM            | All ErlangVM       | Linux, Windows, Mac | All JVM           | All JVM            

---
## Languages

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Primary             | Scala              | Erlang             | Go                 | Java               | Java               
Supported           | Java,Go,C/C++,.NET,Python:two: | Java, .NET, Ruby, Python, JS, Rust, Go, C/C++ | Java, NodeJS, Scala, Python, Ruby | Java, Go, Python, C++, C#, NodeJs, Rust, Erlang |
Client API          | Kafka, Kafka Streams | JMS, AMQP        | NATS               | Pulsar             | JMS, AMQP, ActiveMQ

---

## Resources

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Easy-to-use API     | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb:             | :bulb::bulb::bulb: | :bulb::bulb::bulb:
Documentation       | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb:             | :bulb::bulb::bulb: | :bulb::bulb::bulb:
Tutorials           | :bulb::bulb:       | :bulb::bulb:       | :bulb:             | :bulb::bulb:       | :bulb::bulb::bulb:
YouTube             | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb::bulb:       | :bulb:             | :bulb::bulb::bulb:
Public References   | https://kafka.apache.org/powered-by | T-Mobile, ++ | CloudFoundry  | Yahoo. TenCent, Verizon, Comcast |

---
## Architecture

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Model               | Topics+Partitions  | Exchanges+Queues   |                    | Topics             | Exchanges+Queues
CAP Theorem         | AP                 | CP / AP :seven:    | AP                 |                    | AP
At-most-Once        | :x:                | :heavy_check_mark: | :heavy_check_mark: | :x:                | :x:
At-least-Once       | :heavy_check_mark: | :heavy_check_mark: | :x:                | :heavy_check_mark: | :heavy_check_mark: 
Exactly-Once        | :x:                | :x:                | :x:                | :x:                | :x:
Scale Out           | :heavy_check_mark: | :question:         | :heavy_check_mark: | :heavy_check_mark: |
Pub/Sub             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: 
Distrbuted Queues   | :heavy_check_mark: | :x:                | :heavy_check_mark: | :heavy_check_mark: |
Auto-create Queues  | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: 
Temporary Queues    | :x:                | :heavy_check_mark: |                    |                    | :heavy_check_mark::question:
Request/Reply       | :x:                | :x:                | :heavy_check_mark: |                    | :x:
Idempotent support  | Headers & Keys     | Headers & Keys     |                    |                    |
Message Retention   | :heavy_check_mark: | :heavy_check_mark: | :x:                | :heavy_check_mark: |
Persistence         | File               | JDBC               | :x:                | File               | File (KahaDB) / JDBC
Message Ordering    | In partition only  | :heavy_check_mark: |                    |                    | 
State model         | SQL-like, Windowing| :x: (external)     |                    | SQL-like (external Presto needed)  | :x:
Light-weight        | :x:                | :x:                | :heavy_check_mark: | :x:                | :x:
Independent         | No, Zookeeper:one: | No, if persistence | :heavy_check_mark: | Zookeeper, BookKeeper |
Link to Doc         |                    |                    |                    | [:bookmark_tabs:](https://pulsar.apache.org/docs/en/concepts-architecture-overview) |

---

## Data Formats

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Native types        | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    
Composite types     | client-responsible |                    |                    | avro, protobuf     |                    

---

## Robustness

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
System-Fault Tolerant|:heavy_check_mark: |                    |                    | :heavy_check_mark: | :x:                
Jepsen              | [:bookmark_tabs:](https://aphyr.com/posts/293-call-me-maybe-kafka) | [:bookmark_tabs:](https://aphyr.com/posts/315-call-me-maybe-rabbitmq) | :x: | :x: | :x: 
Jepsen for Zookeeper | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) | :x: | :x: | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) | :x:

---

## Performance

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Msg/sec :three:       | 800,000            | 15,000             | 2,000,000        |               :six:|  25,000            
Max Latency :three:   | 1,000 ms :five:    | 5,000 ms :four:    | 0.3ms            | ~5 ms         :six:|                    
Max Topics/Queues   | 10s of thousands   |                    |                    | 2.8 million/namespace :six:|                    
Max Messages/Queue  | billions           |                    |                    | billions           |                    
Max MB/Queue        | :question:         |                    |                    |                    |                    

---

## Integration

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
MQTT                | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: 
PLCs                | :heavy_check_mark: |                    |                    | :x:                | :x:                
Apache Flink        | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    
Apache Spark        | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    
Apache Hadoop       | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    

---

## Security

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Topic/Queue ACLs    | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    
Roles               | :heavy_check_mark: |                    |                    | :question:       : |                    
Groups              | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    
Network Encryption  | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    
Storage Encryption  | :question:         | :question:         |                    | :heavy_check_mark: |                    

---

## Monitoring

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
JMX                 | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: 
Web UI              | Kowl               | :heavy_check_mark: |                    |                    | :heavy_check_mark: 

---

## Operations

|                   | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Installation        | :thumbsdown: | :thumbsdown::thumbsdown::thumbsdown: | | :thumbsdown::thumbsdown: | :thumbsdown::thumbsdown::thumbsdown:
Daily Maintenance   | None               |                    |                    | None               |                    
Weekly Maintenance  | :question:         | :question:         |                    | :question:         |                    
Software Upgrades   | :x:                | :heavy_check_mark: |                    | :heavy_check_mark: |                    
Machine Upgrades    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    
Contingency Testing | :x:                |                    |                    |                    |                    
Disaster Recovery   | :x:                |                    |                    |                    |                    

---

## Notes
:one: Zookeeper is being phased out and soon no longer needed. A fully HA Zookeeper needs 5 instances, although a 3 instances compromise could be suitable if only running Kafka with Zookeeper.

:two: The border between Apache community and Confluent (the main commercial backer) is quite vague. The Apache community is listed in Maven Central for Java and Scala clients. The others have their GitHub repositories not under Apache.

:three: https://bravenewgeek.com/dissecting-message-queues/

:four: RabbitMQ exposes a linear latency increase with number of processed messages, and 5(!) seconds is reached at 500,000 messages.

:five: Kafka exposes a linear latency increase with number of processed messages and 1 (!) second is reached at about 1 million messages.

:six: Pulsar performance is self-claimed numbers.

:seven: RabbitMQ "Clustering Mode" is CP. RabbitMQ "Shovel" and "Federation" is AP. However the AP modes have non-desirable side effects, such as "A client connecting to any broker can only see queues in that broker." which means that clients needs to understand topology and queue routing.

