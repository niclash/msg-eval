


Unconditionals      | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Community           | Apache             |                    | Linux Foundation   | Apache             | Github
License             | ALv2               | MPL                | ALv2               | ALv2               | MIT
Community Support   | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb::bulb:       | :bulb::bulb:       | :bulb:
Commercial Support  | :heavy_check_mark: Confluent | :heavy_check_mark: VMware | :heavy_check_mark: Synadia Communic. | :heavy_check_mark: RedHat, ++ | :x: 
Operating System    | All JVM            | All ErlangVM       | Linux, Windows, Mac | All JVM            | Linux, Windows

Languages           | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Primary             | Scala              | Erlang             | Go                 | Java               | Go
Supported           | Java,Go,C/C++,.NET,Python:two: |                    | Java, NodeJS, Scala, Python, Ruby |                    |
Other               |                    |                    |                    |                    |
                    
Resources           | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Easy-to-use API     | :bulb::bulb::bulb: | :bulb::bulb::bulb: | :bulb:             |                    |
Documentation       | :bulb::bulb::bulb: |                    | :bulb:             | :bulb::bulb::bulb: | :bulb:
Tutorials           | :bulb::bulb::bulb: |                    | :bulb:             |                    |
YouTube             | :bulb::bulb::bulb: |                    | :bulb::bulb:       |                    |
Public References   | https://kafka.apache.org/powered-by | T-Mobile, ++ | CloudFoundry  |                    |
                    
Architecture        | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Model               | Brokers            | Brokers            |                    | Brokers            |
Stand-Alone         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: 
Scale Out           | :heavy_check_mark: | Bolted On(?)       | :heavy_check_mark: |                    |
Pub/Sub             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:
Distrbuted Queues   | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    
On-the-fly Queues   | :heavy_check_mark: |                    |                    |                    |
Temporary Queues    | :x:                |                    |                    |                    |
Request/Reply       | :x:                | :x:                | :heavy_check_mark: | :x:                | :x:
Persistence         | File               | RDBMS              | :x:                |                    |                    
State model         | SQL-like           |                    |                    |                    |                    
CAP Theorem         | AP                 |                    | AP                 |                    |                    
Light-weight        | :x:                | :x:                | :heavy_check_mark: | :x:                | :heavy_check_mark:                   
Cloud Native        | :x:                | :x:                |                    |                    |                    

Data formats        | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Native types        | :heavy_check_mark: |                    |                    |                    |                    
Composite types     | :heavy_check_mark: |                    |                    |                    |                    
JSON built-in       | :heavy_check_mark: |                    |                    |                    |                    
XML built-in        |                    |                    |                    |                    |                    

Reliability         | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
At-least-once       | :heavy_check_mark: |                    |                    |                    
Idempotent support  | Headers, Keys      |                    |                    |                    
Indepentent         | No, Zookeeper:one: |                    |                    |                    

Robustness          | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
System-Fault Tolerant|:heavy_check_mark: |                    |                    |                    |                    
Software Upgrades   |                    |                    |                    |                    |                    
Hardware Upgrades   |                    |                    |                    |                    |                    

Performance         | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Msg/sec :tre:       | 80,000             | 15,000             | 200,000            | 25,000             | 10,000             
Max Latency :tre:   | 1,000 ms :five:    | 300 ms             | 0.3ms              | 5,000 ms :four:    | 100ms              
Max Topics/Queues   |                    |                    |                    |                    |                    
Max Messages/Queue  |                    |                    |                    |                    |                    
Max MB/Queue        |                    |                    |                    |                    |                    

Integration         | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
MQTT                |                    |                    |                    |                    |                    
PLCs                |                    |                    |                    |                    |                    
Apache Flink        |                    |                    |                    |                    |                    
Apache Spark        |                    |                    |                    |                    |                    
Apache Hadoop       |                    |                    |                    |                    |                    

Security            | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Topic/Queue ACLs    |                    |                    |                    |                    |                    
Roles               |                    |                    |                    |                    |                    
Groups              |                    |                    |                    |                    |                    
Network Encryption  |                    |                    |                    |                    |                    
Storage Encryption  |                    |                    |                    |                    |                    

Monitoring          | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
JMX                 |                    |                    |                    |                    |                    
SNMP                |                    |                    |                    |                    |                    
Web UI              |                    |                    |                    |                    |                    
Custom Alerts       |                    |                    |                    |                    |                    

Operations          | Kafka              | RabbitMQ           | NATS               | ActiveMQ           | NSQ                
--------------------|--------------------|--------------------|--------------------|--------------------|--------------------
Daily Maintenance   |                    |                    |                    |                    |                    
Weekly Maintenance  |                    |                    |                    |                    |                    
Software Upgrades   |                    |                    |                    |                    |                    
Machine Upgrades    |                    |                    |                    |                    |                    
Contingency Testing |                    |                    |                    |                    |                    
Disaster Recovery   |                    |                    |                    |                    |                    

## Notes
:one: Zookeeper is being phased out and soon no longer needed. A fully HA Zookeeper needs 5 instances, although a 3 instances compromise could be suitable if only running Kafka with Zookeeper.

:two: The border between Apache community and Confluent (the main commercial backer) is quite vague. The Apache community is listed in Maven Central for Java and Scala clients. The others have their GitHub repositories not under Apache.

:three: https://bravenewgeek.com/dissecting-message-queues/

:four: RabbitMQ exposes a linear latency increase with number of processed messages, and 5(!) seconds is reached at 500,000 messages.

:five: Kafka exposes a linear latency increase with number of processed messages and 1 (!) second is reached at about 1 million messages.
