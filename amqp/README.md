# Understanding: AMQP

## Overview

[AMQP][amqp], or **Asychronous Message Queueing Protocol**, is an openly published, wire specification for an asynchronous messaging system. This means that that every byte of transmitted data specified. This has allowed libraries to be written in many languages, on multiple operating systems, running on multiple CPU architectures, leading to a truly interoperable, cross platform messaging standard.

In the Java community, the most common messaging system known is [JMS (Java Message Service)][jms]. JMS and AMQP are often compared in Java developer circles. A keen limitation of JMS is that the APIs are specified, but the format of the messages is not. There is no requirement on how the messages are actually formed and transmitted.

The differences between AMQP and JMS can perhaps best be highlighted by the fact that [Pivotal][pivotal] has released a JMS on Rabbit project, a library that implements the JMS APIs but uses RabbitmQ, an AMQP broker to actually transport the messages.

AMQP [publishes it's specifications][amqp-spec] in a downloadable, XML format. This has made it easy for library maintainers to generate APIs driven by these specs while also automating construction of algorithms to marshal and demarshal messages.

That combined with the openness of the spec has led to the rise of multiple brokers supporting AMQP. Here are some:
- [RabbitMQ][rabbitmq]
- [ActiveMQ][activemq]
- [Qpid][qpid]

## Comparison between AMQP and JMS

Developers familiar with [JMS][jms] may encounter confusing usage of terms when they start using an AMQP-based message solution.

- JMS has queues and topics. A message sent on a JMS queue will be consumed by no more than one client. A message sent on a JMS topic may be consumed by multiple consumers. AMQP only has queues. A message sent on an AMQP queue may reach one or more consumers.
- JMS and AMQP both have an equivalent message header, providing the means to sort and route messages.
- JMS and AMQP both have brokers responsible for receiving, routing, and ultimately dispensing messages to consumers.
- AMQP has exchanges and routes. Messages are published to exchanges. Routes define on which queue(s) to publish the message.

[amqp]: http://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol
[jms]: http://en.wikipedia.org/wiki/Java_Message_Service
[amqp-spec]: http://www.amqp.org/resources/download
[pivotal]: http://gopivotal.com
[rabbitmq]: http://rabbitmq.com
[activemq]: http://activemq.apache.org/
[qpid]: http://qpid.apache.org/index.html

