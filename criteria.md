# Criteria of Message System Evaluation

We need to establish a evaluation framework, where we list all the relevant aspects
of an enterprise messaging system as a neutral ground and then acquire the information
about each of the systems to be evaluated.

## Terminology
  * Producer - A client to the messaging system that publish messages to one or more topics.
  * Consumer - A client that reads messages from one or more topics.
  * Consumer Group - A set of client instances that read the SAME topic(s) without getting the same message twice.
  * Topic - A named "channel" through which messages are traveling from producer to consumer.
  * Sub-topic - Topics organized in a tree hierarchy, where a consumer can read messages from a partial tree.
  
## Unconditionals

### Open Source
All systems to be considered must be Open Source Software with a license that allows
enterprise development and not risk exposing enterprise proprietary software to have
to be published.

### Supported
All systems to be considered must have both a strong community that support the product
as well as paid-for commercial support with possible/optional service agreements.

### Stand-Alone
There are messaging systems (e.g. ZeroMQ) that are embedded into the applications themselves.
Such embedding have some technical pros and cons, but more importantly, it blows security
right out of the water, as rogue app developers could plant trojan horses that get access
to sensitive data much more easily than a stand alone system.

### Scalable
The system must be able to scale out to a large number of topics/queues, with many messages
per topic/queue and high throughput of messages. This more or less requires a distributed
solution, so standalone applications with a CA (no Partition Tolerance) are excluded by default.

## Evaluation Categories

### Primary Language(s)
Which language(s) is(are) the system written in? This revolves around the remote possibility that
we will need to troubleshoot, fix/patch and dig deep into the source code of the system. Major
languages are required, such as Java, C/C++, C#, Python and others. 

### Supported Language(s)
Which languages are used in clients (producers, consumers) and supported by the core developers. This
typically includes client API libraries in these languages to simplify software development, and we
are here looking for the languages that are supported out-of-the-box, the language(s) used in tutorials
and on Stack Overflow when most people are asking questions.

### Community Languages
Additional languages that are supported by community members, and some support can be found on the net.

### API Ease-of-use
Subjective evaluation on how difficult a API is to use. It also includes whether JMS (Java Message Service)
is offered by default, which simplifies things a lot for less experienced Java developers.
Things being considered are not only how the "happy path" is accessed, but what programmers need to do
when something goes wrong, such as reconnects, posting to deadletter queues, et cetera.

### Architecture 
Under Architecture, we are going to look at the overall philosophy, design priorities and compromises made
in each system.

#### Broker/Brokerless
Brokerless architecture is already out of the question, for security reasons listed in "Unconditionals" above.

#### Pub/Sub philosophy
There are different modeling paradigms in this space. Queues vs Topics. Partitioned operations, or not. Whether
the broker or the consumer is responsible for knowing where in the queue/topic the next message is, and many
other aspects. Are messages just a blob of bytes, is there a Key associated, any metadata/headers?

#### Persistence
Messaging systems need persistence, to ensure that published messages are reaching the consumers/subscribers.
There are several different approaches to how persistence is achieved.

#### Stateful/Stateless
We will try to evaluate how stateful or stateless each system is. For instance, Kafka can keep aggregated states
of topics and such state can be queried (SQL-like).

#### CAP Theorem
CAP Theorem applies to messaging systems and we are only going to look at CP and AP systems, and find out
whether there is flexibility in that (e.g. Apache Cassandra can set CP or AP per transaction rather than the
configuration of the servers)

#### Stream Processing
Does the messaging system have any additional support built-in for stream processing?

#### Consumer Groups
Are consumer groups supported out of the box, or do we need to find a solution on top?

#### Producers
How does the system handle multiple producers to the same topic? Ordering? Guarantees? Deadlocks?

#### Cloud native
How difficult is it to run this on Kubernetes or similar system? Are kubelets available from the community?
Can we find solutions on Github?

### Data Formats
Most messaging systems can transport bytes. Here we need to look into how much serialization support is
included out-of-the-box, rather than relying on programmers deploying a solution on top.

### Reliability
Reliability refers to the tendency for the system to deliver each message once and only once. Few 
distributed systems can guarantee once and only once (no matter fault situations) semantics. But client
side APIs can assist in simplifying the net result of "once and only once". So will look at 
"Message Loss" possibilities in the system itself, and look at built-in support of "De-duplication" of 
messages.


### Robustness
Robustness (unlike Reliability) is about the ability of the system to withstand failures. Some failures
come from hardware breaking down, doing the wrong thing or network packets being lost or misrouted. Other
failures are planned, such as machine/host replacements, software upgrades and contingency planning/testing.

Jepsen relevant reports.
  * https://aphyr.com/posts/293-call-me-maybe-kafka
  * https://aphyr.com/posts/315-call-me-maybe-rabbitmq
  * https://aphyr.com/posts/291-call-me-maybe-zookeeper


#### System Fault Tolerance (SFT)
SFT refers to the ability of a system to withstand a random event causing parts of a system to fail. At the
minimum is "broken harddisk" and all the way up to "datacenter exploded/burned to the ground" (Happened 
recently in France). We will look a Jepsen.io, an independent researcher/tester (available for hire) that 
try to break these robust systems and generates very specific reports on where they don't perform as advertised.

#### Software Upgrade without downtime
That we write client applications that can be upgraded in a rolling fashion is a challenge in itself. It will
help if there is additional support in the messaging system to handle members in consumer groups being 
replaced in somewhat rapid succession. Difficult to evaluate!

Then there is the issue of being able to upgrade the brokers themselves in a rolling fashion, without downtime.
This might be advertised as "Yes", but one should look at previous upgrades, especially between MAJOR versions
(such as 1.2 -> 2.0) and go through the Migration documents for those. Also not easy to evaluate!


#### Hardware changes without downtime
If the messaging system is System Fault Tolerant, then hardware changes could be a matter of 
"turn on new machine and configure" and then "turn off existing machine". 
If running in a Kubernetes environment, this might be a moot point.


### Performance
  * Messages/Sec
  * Max Latency
  * Max Number of Topics
  * Max Messages in Topic
  * Max data in Topic
  * Scale Out?

### Integration
Obviously we can create applications that uses the messaging system, but sometimes it is better to
use off-the-shelf solution to integrate with other systems and not having to worry about messaging details
and instead focus on the business values.

The more integrations that are available, relevant to the business, the more interesting the messaging system
becomes.

#### MQTT - Mosquitto
MQTT is a light-weight messaging protocol, typically used for communicating sensor/actuator data in a M2M manner.
Mosquitto is one of the most popular and robust open source solutions, and it would be beneficial if we 
get the integration without coding.

#### PLCs  
PLCs (Programmable Logic Controllers) are automation devices that connects to the real world, to sensors, actuators,
valves and so forth. We anticipate that there might be a need to be able to interface with PLCs.

There are many legacy protocols in this space, although some are more prevalent than others.
It would be beneficial if we can configure the messaging system to send data to and receive data from such PLCs
without having to learn these protocols and cater for all the perculiarities that are associated with them.

#### Apache Flink
Flink is a stream processing platform, almost like Amazon Lambda. A topology is defined in a declarative fashion, 
which is then uploaded to Flink that executes the topology on available hardware resources at quite incredible 
scales. Programming model might not be ideal, handling deployment becomes a joy.

#### Apache Spark
Spark is similar to Flink, but uses a "batch model" combined with "real-time"-ish data. Flink supports the 
batch model, called "windowing", for streams but Spark is more suitable when other batch data algorithms are
combined with stream processing.

#### Apache Hadoop
Hadoop is, as most people know, a batch processing platform. If the messaging system has support for Hadoop/HDFS
sources/destinations then that could very well be beneficial for various reasons.

### Security
Some of the data might be critical to functional society and security must not be taken lightly. We want to see
the messaging system has built-in support for;
  * ACLs
  * Roles
  * Groups
  * (Sub)Topic protection

And if any of these are missing, then we need to look at the specifics in great detail of what may be acceptable.

### Monitoring
Operations need to have good overview of the running applications and the platforms involved. The messaging system
should preferably integrate into existing monitoring solution (TBD what that is). At minimum, we need;
  * JMX (if Java app)
  * SNMP (if not Java app)
  * Web UIs (for details to humans)
  

### Operations / Run books
Once a system is running in production, we need to take care of it. We will look at common run book operations each
of the system will require, how easy/hard it is to do software and hardware upgrades and other maintenance tasks.
  * Daily Maintenance (preferably none)
  * Weekly Maintenance (if any)
  * Maintenance triggered by alerts
  * Software Upgrades
  * Machine Upgrades

#### Disaster Recovery
We will try to look into worst-case scenarios and how Disaster Recovery procedures may look like.

  
## Preliminary Round
The following systems have been identified through personal experience and Google Search. So let's get their own
pitches and then we will filter out those that don't fulfill the __Unconditionals__ above
  * RabbitMQ
  * Apache Kafka
  * Apache ActiveMQ
  * Apache RocketMQ
  * Celery
  * NSQ
  * Redisson
  * NATS
  * KubeMQ

### RabbitMQ (passes)

### Apache Kafka  (passes)
### Apache ActiveMQ Artemis (passes)
ActiveMQ Artemis is the "next generation" of ActiveMQ, and will eventually replace "Classic".

High-performance, non-blocking architecture for the next generation of messaging applications.

  * JMS 1.1 & 2.0 + Jakarta Messaging 2.0 & 3.0 with full client implementations including JNDI
  * High availability using shared storage or network replication
  * Simple & powerful protocol agnostic addressing model
  * Flexible clustering for distributing load
  * Advanced journal implementations for low-latency persistence as well as JDBC
  * High feature parity with ActiveMQ "Classic" to ease migration
  * Asynchronous mirroring for disaster recovery
  * Data Driven Load Balance

### Apache RocketMQ (passes)
### Celery (don't pass)
### NSQ (don't pass)
### Redisson (don't pass)
### NATS (passes)
### KubeMQ (don't pass)
