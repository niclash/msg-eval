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
#### MQTT - Mosquitto
#### Apache Flink
#### Apache Spark
#### Apache Hadoop
  


### Security
  ACLs
  Roles
  Groups
  (Sub)Topic protection
  
### Monitoring
  JMX
  SNMP
  Web UIs
  

### Operations / Run books
  Daily Maintenance
  Weekly Maintenance
  Software Upgrades
  Machine Upgrades
  

### Messaging systems to evaluate
  * Kafka
  * RabbitMQ
  * ActiveMQ
  * RocketMQ
