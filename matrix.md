


Unconditionals      | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Community           | Apache             |                    | Linux Foundation   | Apache             | Apache             
License             | ALv2               | MPL                | ALv2               | ALv2               | ALv2               
Community Support   | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb::bulb:       | :bulb::bulb:       | :bulb::bulb:       
Commercial Support  | :heavy_check_mark: Confluent | :heavy_check_mark: VMware | :heavy_check_mark: Synadia Communic. |  | :heavy_check_mark: RedHat, ++ 
Operating System    | All JVM            | All ErlangVM       | Linux, Windows, Mac | All JVM           | All JVM            

---

Languages           | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Primary             | Scala              | Erlang             | Go                 | Java               | Java               
Supported           | Java,Go,C/C++,.NET,Python:two: |                    | Java, NodeJS, Scala, Python, Ruby |                    |
Other               |                    |                    |                    |                    |                    
Client API          | Kafka, Kafka Streams | Rabbit, JMS      | NATS               | Pulsar             | JMS, ?

---

Resources           | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Easy-to-use API     | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb:             | :bulb::bulb::bulb: | :bulb::bulb::bulb:                   
Documentation       | :bulb::bulb::bulb: |                    | :bulb:             | :bulb::bulb::bulb: | :bulb::bulb::bulb: 
Tutorials           | :bulb::bulb::bulb: |                    | :bulb:             |                    |                    
YouTube             | :bulb::bulb::bulb: |                    | :bulb::bulb:       | :bulb:             |                    
Public References   | https://kafka.apache.org/powered-by | T-Mobile, ++ | CloudFoundry  | Yahoo  |                    |

---

Architecture        | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Model               | Brokers            | Brokers            | Brokers            | Brokers            | Brokers            
CAP Theorem         | AP                 |                    | AP                 |                    |                    
At-most-Once        | :x:                | :heavy_check_mark: | :heavy_check_mark: | :x:                | :x:                
At-least-Once       | :heavy_check_mark: | :heavy_check_mark: | :x:                | :heavy_check_mark: | :heavy_check_mark: 
Exactly-Once        | :x:                | :x:                | :x:                | :x:                |                 
Scale Out           | :heavy_check_mark: | Bolted On(?)       | :heavy_check_mark: | :heavy_check_mark: |                    
Pub/Sub             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: 
Distrbuted Queues   | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    
Auto-create Queues  | :heavy_check_mark: |                    |                    |                    |                    
Temporary Queues    | :x:                |                    |                    |                    |                    
Request/Reply       | :x:                | :x:                | :heavy_check_mark: |                    | :x:                
Idempotent support  | Headers & Keys     | Headers & Keys     |                    |                    |                    
Persistence         | File               | RDBMS              | :x:                | File               |                    
State model         | SQL-like           |                    |                    | SQL-like (external Presto needed)  |                    
Light-weight        | :x:                | :x:                | :heavy_check_mark: | :x:                | :x:                                  
Independent         | No, Zookeeper:one: |                    | :heavy_check_mark: | Zookeeper, BookKeeper |                    
Cloud Native        | :x:                | :x:                |                    |                    |                    
Link to Doc         |                    |                    |                    | [:bookmark_tabs:](https://pulsar.apache.org/docs/en/concepts-architecture-overview) |

---

Data formats        | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Native types        | :heavy_check_mark: |                    |                    |                    |                    
Composite types     | :heavy_check_mark: |                    |                    |                    |                    
JSON built-in       | :heavy_check_mark: |                    |                    |                    |                    
XML built-in        |                    |                    |                    |                    |                    

---

Robustness          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
System-Fault Tolerant|:heavy_check_mark: |                    |                    |                    |                    
Jepsen              | [[:bookmark_tabs:](https://aphyr.com/posts/293-call-me-maybe-kafka) | [:bookmark_tabs:](https://aphyr.com/posts/315-call-me-maybe-rabbitmq) | | | 
Jepsen for Zookeeper | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) | | | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) |

---

Performance         | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Msg/sec :tre:       | 800,000            | 15,000             | 2,000,000          |               :six:|  25,000            
Max Latency :tre:   | 1,000 ms :five:    | 5,000 ms :four:    | 0.3ms              | ~5 ms         :six:|                    
Max Topics/Queues   | 10s of thousands   |                    |                    |               :six:|                    
Max Messages/Queue  | billions           |                    |                    |                    |                    
Max MB/Queue        | :question:         |                    |                    |                    |                    

---

Integration         | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
MQTT                | :heavy_check_mark: |                    |                    |                    |                    
PLCs                | :heavy_check_mark: |                    |                    |                    |                    
Apache Flink        | :heavy_check_mark: |                    |                    |                    |                    
Apache Spark        | :heavy_check_mark: |                    |                    |                    |                    
Apache Hadoop       | :heavy_check_mark: |                    |                    |                    |                    

---

Security            | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Topic/Queue ACLs    | :heavy_check_mark: |                    |                    |                    |                    
Roles               | :heavy_check_mark: |                    |                    |                    |                    
Groups              | :heavy_check_mark: |                    |                    |                    |                    
Network Encryption  | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    
Storage Encryption  | :question:         |                    |                    |                    |                    

---

Monitoring          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
JMX                 | :heavy_check_mark: |                    |                    |                    |                    
SNMP                | :x:                |                    |                    |                    |                    
Web UI              | Kowl               | :heavy_check_mark: |                    |                    |                    
Custom Alerts       | :question:         |                    |                    |                    |                    

---

Operations          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Installation        | :thumbsdown: | :thumbsdown::thumbsdown::thumbsdown: | | :thumbsdown::thumbsdown: | :thumbsdown::thumbsdown::thumbsdown:
Daily Maintenance   | None               |                    |                    | None               |                    
Weekly Maintenance  | :question:         |                    |                    |                    |                    
Software Upgrades   | :heavy_check_mark: |                    |                    |                    |                    
Machine Upgrades    | :heavy_check_mark: |                    |                    |                    |                    
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
