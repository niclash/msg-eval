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

### Documentation / Resources
All open source projects gets a lot of documentation critique. Either there is not enough documentation,
too much documentation or not the right documentation. We will try to evaluate the current situation in
the systems being evaluated.

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
  * 
  * 
  * 


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
  * Network encryption
  * Storage encryption

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
  * Apache Pulsar
  * Celery
  * NSQ
  * Redisson
  * NATS
  * KubeMQ

All product descriptions in the following sections are picked from the projects and
have not be validated.
  
### RabbitMQ (passes)
RabbitMQ is the most widely deployed open source message broker.

With tens of thousands of users, RabbitMQ is one of the most popular open source message brokers. From T-Mobile to Runtastic, RabbitMQ is used worldwide at small startups and large enterprises.

RabbitMQ is lightweight and easy to deploy on premises and in the cloud. It supports multiple messaging protocols. RabbitMQ can be deployed in distributed and federated configurations to meet high-scale, high-availability requirements.

### Apache Kafka  (passes)
More than 80% of all Fortune 100 companies trust, and use Kafka.

Apache Kafka is an open-source distributed event streaming platform used by thousands of companies for high-performance data pipelines, streaming analytics, data integration, and mission-critical applications."

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

![Kafka Architecture](https://cdn.confluent.io/wp-content/uploads/Screenshot-2017-07-19-19.14.28-1024x626.png)

### Apache Pulsar (passes)
Apache Pulsar is a cloud-native, distributed messaging and streaming platform originally created at Yahoo! 
and now a top-level Apache Software Foundation project

![Pulsar Architecture](https://pulsar.apache.org/docs/assets/pulsar-system-architecture.png)

### Celery (don't pass)
Celery is a simple, flexible, and reliable distributed system to process vast amounts 
of messages, while providing operations with the tools required to maintain such a system.
It’s a task queue with focus on real-time processing, while also supporting task scheduling.

Rejected; It is an application on top of messaging systems and has a very specific focus
which we may or may not need. But we can always come back after selecting messaging system
as it seems to support most.

### NSQ (doesn't pass)
A realtime distributed messaging platform.
  * Distributed - NSQ promotes distributed and decentralized topologies without single points of failure, enabling fault tolerance and high availability coupled with a reliable message delivery guarantee. See features & guarantees.

  * Scalable - NSQ scales horizontally, without any centralized brokers. Built-in discovery simplifies the addition of nodes to the cluster. Supports both pub-sub and load-balanced message delivery. It’s fast, too.

  * Ops Friendly - NSQ is easy to configure and deploy and comes bundled with an admin UI. Binaries have no runtime dependencies and we provide pre-compiled releases for linux, darwin, freebsd and windows as well as an official Docker image.

  * Integrated - Official Go and Python libraries are available as well as many community supported libraries for most major languages (see client libraries). If you’re interested in building your own, there’s a protocol spec.

Rejected: Seemingly no commercial support available
  
### Redisson (doesn't pass)
(no slogan, self-promote found. So my own words.)
Redisson is a Java client for Redis and has built-in distributed data structures, incl queues.

Rejected; Security reasons.

### NATS (passes)
Connective Technology for Adaptive Edge & Distributed Systems


  * Agile - With flexible deployments models using clusters, superclusters, and leaf nodes, optimize communications for your unique deployment. The NATS Adaptive Edge Architecture allows for a perfect fit for unique needs to connect devices, edge, cloud or hybrid deployments.

  * Secure - With true multi-tenancy, securely isolate and share your data to fully meet your business needs, mitigating risk and achieving faster time to value. Security is bifurcated from topology, so you can connect anywhere in a deployment and NATS will do the right thing.
  
  * Performant - With the ability to process millions of messages a second per server, you’ll find unparalleled efficiency with NATS. Save money by minimizing cloud costs with reduced compute and network usage for streams, services, and eventing.
  
  * Resilient - NATS self-heals and can scale up, down, or handle topology changes anytime with zero downtime to your system. Clients require zero awareness of NATS topology allowing you future proof your system to meet your needs of today and tomorrow.
  
NOTE: During compilation of NATS features and performance, it came to the forefront that it is a "At-Most-Once" system, i.e. handing over a message to a broker doesn't guarantee that consumers will get the messsage, due to lacking persistence system. This is probably also the reason that performance is quite outstanding. So, we are not completing the matrix for NATS for now, until we come across a usecase where that limitations is not of importance and speed is paramount. I also don't think that it is possible to plug Persistence into it, except modifying source code, and that is beyond our scope.  

### KubeMQ (doesn't pass)
An Open-Source, Kubernetes-Native Messaging Platform

A message broker and message queue ideal for developers. Provides all messaging 
patterns, scalable, highly available, and secure. Connect microservices instantly 
using a rich set of connectors without writing any code. Easy-to-use SDKs and 
elimination of predefined topics, channels, brokers, and routes.

![KubeMQ Architecture](https://kubemq.io/wp-content/uploads/2020/08/kubemq_diagram_1100w_nomargin.png)

Rejected; KubeMQ is with a Freemium model, and that typically means that enterprise needs
(such as production monitoring, how many instances, ++) will require a paid-for license and 
all source is not available.

