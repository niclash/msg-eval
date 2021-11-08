


Unconditionals      | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Community           | Apache             |                    | Linux Foundation   | Apache             | Apache             | Github
License             | ALv2               | MPL                | ALv2               | ALv2               | ALv2               | MIT
Community Support   | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb::bulb:       | :bulb::bulb:       | :bulb::bulb:       | :bulb:
Commercial Support  | :heavy_check_mark: Confluent | :heavy_check_mark: VMware | :heavy_check_mark: Synadia Communic. |  | :heavy_check_mark: RedHat, ++ | :x: 
Operating System    | All JVM            | All ErlangVM       | Linux, Windows, Mac | All JVM           } All JVM            | Linux, Windows

Languages           | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Primary             | Scala              | Erlang             | Go                 | Java               | Java               | Go
Supported           | Java,Go,C/C++,.NET,Python:two: |                    | Java, NodeJS, Scala, Python, Ruby |                    |                    |
Other               |                    |                    |                    |                    |                    |
                    
Resources           | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Easy-to-use API     | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb:             |                    |                    |
Documentation       | :bulb::bulb::bulb: |                    | :bulb:             |                    | :bulb::bulb::bulb: | :bulb:
Tutorials           | :bulb::bulb::bulb: |                    | :bulb:             |                    |                    |
YouTube             | :bulb::bulb::bulb: |                    | :bulb::bulb:       |                    |                    |
Public References   | https://kafka.apache.org/powered-by | T-Mobile, ++ | CloudFoundry  | Yahoo  |                    |
                    
Architecture        | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Model               | Brokers            | Brokers            | Brokers            | Brokers            | Brokers            |
CAP Theorem         | AP                 |                    | AP                 |                    |                    |                    
At-most-Once        | :x:                | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    
At-least-Once       | :heavy_check_mark: | :heavy_check_mark: | :x:                |                    |                    |  
Exactly-Once        | :x:                | :x:                | :x:                |                    |                    |                    
Scale Out           | :heavy_check_mark: | Bolted On(?)       | :heavy_check_mark: |                    |                    |
Pub/Sub             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark:
Distrbuted Queues   | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    
On-the-fly Queues   | :heavy_check_mark: |                    |                    |                    |                    |
Temporary Queues    | :x:                |                    |                    |                    |                    |
Request/Reply       | :x:                | :x:                | :heavy_check_mark: |                    | :x:                | :x:
Persistence         | File               | RDBMS              |                    |                    |                    |                    
State model         | SQL-like           |                    |                    |                    |                    |                    
Light-weight        | :x:                | :x:                | :heavy_check_mark: |                    | :x:                | :heavy_check_mark:                   
Cloud Native        | :x:                | :x:                |                    |                    |                    |                    
Link to Doc         |                    |                    |                    | [:bookmark_tabs:](https://pulsar.apache.org/docs/en/concepts-architecture-overview) |  |

Data formats        | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Native types        | :heavy_check_mark: |                    |                    |                    |                    |                    
Composite types     | :heavy_check_mark: |                    |                    |                    |                    |                    
JSON built-in       | :heavy_check_mark: |                    |                    |                    |                    |                    
XML built-in        |                    |                    |                    |                    |                    |                    

Reliability         | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
At-least-once       | :heavy_check_mark: |                    |                    |                    |                    
Idempotent support  | Headers, Keys      |                    |                    |                    |                    
Independent         | No, Zookeeper:one: |                    | :heavy_check_mark: | Zookeeper, BookKeeper |                    |                    

Robustness          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
System-Fault Tolerant|:heavy_check_mark: |                    |                    |                    |                    |                    
Software Upgrades   |                    |                    |                    |                    |                    |                    
Hardware Upgrades   |                    |                    |                    |                    |                    |                    
Jepsen              | [[:bookmark_tabs:](https://aphyr.com/posts/293-call-me-maybe-kafka) | [:bookmark_tabs:](https://aphyr.com/posts/315-call-me-maybe-rabbitmq) | | | | 
Jepsen for Zookeeper | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) | | | [:bookmark_tabs:](https://aphyr.com/posts/291-call-me-maybe-zookeeper) | |

Performance         | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Msg/sec :tre:       | 800,000            | 15,000             | 2,000,000          |                    |  25,000            | 10,000             
Max Latency :tre:   | 1,000 ms :five:    | 5,000 ms :four:    | 0.3ms              |                    |                    | 100ms              
Max Topics/Queues   |                    |                    |                    |                    |                    |                    
Max Messages/Queue  |                    |                    |                    |                    |                    |                    
Max MB/Queue        |                    |                    |                    |                    |                    |                    

Integration         | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
MQTT                |                    |                    |                    |                    |                    |                    
PLCs                |                    |                    |                    |                    |                    |                    
Apache Flink        |                    |                    |                    |                    |                    |                    
Apache Spark        |                    |                    |                    |                    |                    |                    
Apache Hadoop       |                    |                    |                    |                    |                    |                    

Security            | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Topic/Queue ACLs    |                    |                    |                    |                    |                    |                    
Roles               |                    |                    |                    |                    |                    |                    
Groups              |                    |                    |                    |                    |                    |                    
Network Encryption  |                    |                    |                    |                    |                    |                    
Storage Encryption  |                    |                    |                    |                    |                    |                    

Monitoring          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
JMX                 |                    |                    |                    |                    |                    |                    
SNMP                |                    |                    |                    |                    |                    |                    
Web UI              |                    |                    |                    |                    |                    |                    
Custom Alerts       |                    |                    |                    |                    |                    |                    

Operations          | Kafka              | RabbitMQ           | NATS               | Pulsar             | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Daily Maintenance   |                    |                    |                    |                    |                    |                    
Weekly Maintenance  |                    |                    |                    |                    |                    |                    
Software Upgrades   |                    |                    |                    |                    |                    |                    
Machine Upgrades    |                    |                    |                    |                    |                    |                    
Contingency Testing |                    |                    |                    |                    |                    |                    
Disaster Recovery   |                    |                    |                    |                    |                    |                    

## Notes
:one: Zookeeper is being phased out and soon no longer needed. A fully HA Zookeeper needs 5 instances, although a 3 instances compromise could be suitable if only running Kafka with Zookeeper.

:two: The border between Apache community and Confluent (the main commercial backer) is quite vague. The Apache community is listed in Maven Central for Java and Scala clients. The others have their GitHub repositories not under Apache.

:three: https://bravenewgeek.com/dissecting-message-queues/

:four: RabbitMQ exposes a linear latency increase with number of processed messages, and 5(!) seconds is reached at 500,000 messages.

:five: Kafka exposes a linear latency increase with number of processed messages and 1 (!) second is reached at about 1 million messages.
