
# Why Pulsar over Kafka?

Apache Pulsar and Apache Kafka have quite a lot of commonality. They are both targeting high volume messaging systems, in central roles of large/critical systems. They have both simplified the abstraction (compared to AMQP implementations and IBM MQseries).

Both Pulsar and Kafka is hosted by the Apache Software Foundation, and all its projects are licensed under the permissive Apache License version 2.0. This allows us to use the software in any way we see fit, not required to reciprocate in any way, and only limited in regards of trademarks (can't use the Apache trademarks as our own) and some patents restrictions.

They are also both developed and supported by a large, very active and responsive community. And both have commercial support options available from commercial companies, that are strong participants in the Apache community.

## Abstraction
Pulsar supports the same messaging abstractions as Kafka, which is basically only the high volume, stream processing usecase.

But Pulsar has more tricks up its sleeve, and can also be used for traditional messaging systems (normally served by AMQP or MQseries) for EIP (enterprise integration patterns). It is easier to set up Hot/Cold, Hot/Warm and Hot/Hot redundancy (of other, non-HA applications) in Pulsar than it is in Kafka.

Neither Kafka nor Pulsar supports topic hierarchies, like those in AMQP or MQTT.

## Programming Model
Both Kafka and Pulsar have very easy to understand APIs at their core. 

Kafka promotes _Kafka Streams_ as the key programming model, very similar to Java Stream API, and although very easy to understand and use, it becomes a nightmare when something goes wrong. Really hard to troubleshoot.

Pulsar allows 3 tiers; 
    1. directly reading the topic in one's own event loop, 
    1. register a `MessageListener<T>`,
    1. deploy _Pulsar Functions_, the serverless option similar to "AWS Lambda" and "Google Cloud Functions"

The Programming Model includes Schemas (see below) which can also make programming life a lot easier.

## Programming Language
Kafka is mostly written in Scala and any work on the Kafka platform itself requires Scala skills, which is less abundant than Java skills, which is the language of Pulsar.

_Pulsar Functions_ must be written in Java, but otherwise these client languages are supported by community;
  1. Java
  1. Go
  1. Python
  1. C++
  1. C#
  1. NodeJS
  1. WebSockets - Any language that supports WebSockets (i.e. most) can access the core API in Pulsar.

Also, the following languages are supposedly supported by third-party;
  1. Haskell
  1. Scala
  1. Rust
  1. .NET (C#/F#/VB)
       
## Scale Out
Kafka has tied the storage and partition model to each other, which makes it really difficult (rebalance leads to downtime) to change the partitioning later in the system lifecycle. It is recommended that the future max partitions are set up from the start. That is a lose-lose proposal, since on one hand it will be unnecessary with 30 (2*3*5) partitions in the beginning of any system, and might not be enough later. To change the partitions later, a re-balance is needed, and that takes both time (depending on how long detention time is, and how much storage is used) and downtime while it is happening.

By contrast, Pulsar uses Apache Bookkeeper, which is a distributed ledger that takes care of redundant storage. Bookkeeper can be scaled up independently of the Pulsar _brokers_. Need faster/more storage, then scale out Bookkeeper. Need more processing power, then scale out the _brokers_.

So, in Pulsar we can start with 2 partitions (of each topic) and add more over time, as need rises.

## Upgrades
It is easier to upgrade Pulsar+Bookkeeper than it is to upgrade Kafka. Again, this comes back to the design with separation of brokers and storage. Pulsar seems to take upgrades more seriously than Kafka. That said, upgrades are not trivial and efforts are required to set up a process for it.

## Serverless Option
Pulsar has an option to set up _Pulsar Functions_, which turns Pulsar into something similar to AWS Lambda, i.e. serverless deployment of functions, that can be wired together. This option is not available in Kafka and must be built/obtained separately.

Serverless received a lot of hype over the last few years, but it is still unclear whether it is able to live up to the hype. It is good to know that it is available, and can be tried out without large extra cost.

## Multitenancy
Kafka doesn't support multi-tenancy. All topics have a flat name (no hiearchy) and to achieve full topic isolation, one MUST set up multiple clusters.

Pulsar has explicit multi-tenancy support. Each tenant has its own administrator roles, who are free to set up the namespaces as the tenant wishes.

This is essential if we are supporting customer-specific applications running together with the base system.

## Namespaces
Namespaces is a convenient separation of topic naming and security. Kafka doesn't have anything like it.

In Pulsar, it is recommended that each bounded context (or application) has its own namespace, to avoid topic naming conflicts and not having centralized topic management.


## Security
Kafka's security is relatively simple, mostly due to the abstraction being much simpler, and wasn't designed with security as a first-class citizen.

Pulsar has separate security for each _Namespace_, managed by the _administrator_ role of the _Tenant_. 

It seems to be possible to use different authorization keys per topic, with 6 permissions possible on each.

It is not confirmed whether the security system(s) are pluggable, but since most things in Pulsar are, I suspect that this is the case. That should mean that it is possible to integrate firm-wide security systems into Pulsar.

## Schemas
Pulsar has much better schema support. Kafka allows one to implement so called _SerDes_ (Serializer/Deserializer) and use those during producing/consuming messages. There are no safe-guards that the correct ones are used, and it is possible to mix schemas within topics as much as one want. 

In Pulsar, though, schemas are managed. Once a topic is associated with a schema, all future messages in and out of that topic, must either use the same schema or an evolved schema. Otherwise message production/consumption is prohibited.

Schema Evolution means that one is allowed to make compatible changes to existing schemas, and can register new ones with evolutionary rules on how old messages are converted to new ones. This allows long-term storage of some message types, that can evolve as business requirements change.

## Cloud-native
_Cloud-native_ is a term that is thrown around a lot to promote technologies in this day and age. It basically revolves around whether it is hard or easy to deploy and operate an application in cloud environments. For instance, is it fault-tolerant, can it scale on-demand, can it be re-positioned on another VM, and so on.

Kafka was never meant to be cloud-native, and its focus is all on churning as many messages as possible through the system. It expects a relatively stable set up, and shifting around the instances are not expected. Upgrading to new versions is a matter of careful orchestration, and scale is something that is pre-planned.

Pulsar's design with Bookkeeper makes it much more cloud-friendly, although _I_ wouldn't call it cloud-native. A lot of documentation and tooling exist to deploy in a variety of systems, incl bare-metal, docker, DC/OS & Apache Mesos, Kubernetes and AWS/Terraform. Setting up a Pulsar system on bare metal with the help of Ansible is roughly as complex as setting up Kafka.

## Monitoring
Kafka doesn't come with much tools for monitoring. Thurd-party, open source, Kowl is very rudimentary. And the idea is to use JMX. If a JMX tooling stack is already in place, that is fine. But nowadays, modern monitoring uses Grafana and more often than not set up Prometheus for metrics aggregation/database. To use Kafka with Prometheus we need to install a _JMX Exporter_ into the JVM (via the agent API), configured for all the data points (~200 or so) we want to monitor.

Pulsar comes with a rudimentary management tool, but more importantly it supports Prometheus out of the box. This means easier deployment and fewer moving parts that can break.

## Integration
Kafka has a very rich eco-system of integration modules. Pulsar is lacking in this respect, but https://hub.streamnative.io/ shows a decent set, and the more important ones, like MQTT, Cassandra, Flink, Spark, HDFS/Hadoop, are available and ready to use.

## High Availability and Disaster Contingency
Pulsar has, unlike Kafka, explicit support for cross-datacenter replication. In essence, fully replicated setup and automatic fail-over is possible to set up, but requires an additional central Zookeeper cluster that both Pulsar datacenters use. This has not been dug into and it is unclear what possibilities, requirements and limitations are associated with such a setup. The primary purpose is to be resilient to even datacenter outage.

