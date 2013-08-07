# Understanding AMQP

## Overview

[AMQP][amqp] (Asychronous Message Queueing Protocol) is an openly published wire specification for asynchronous messaging. Every byte of transmitted data is specified. This characteristic allows libraries to be written in many languages, and to run on multiple operating systems and CPU architectures, which makes for a truly interoperable, cross-platform messaging standard.

## Advantages of AMQP over JMS

AMQP is often compared to [JMS (Java Message Service)][jms], the most common messaging system in the Java community. A limitation of JMS is that the APIs are specified, but the message format is not. Unlike AMQP, JMS has no requirement for how messages are formed and transmitted.

Thus [Pivotal][pivotal] has released a JMS on Rabbit project, a library that implements the JMS APIs but uses [RabbitMQ][rabbitmq], an AMQP broker, to transmit the messages.

AMQP [publishes its specifications][amqp-spec] in a downloadable XML format. This availability makes it easy for library maintainers to generate APIs driven by the specs while also automating construction of algorithms to marshal and demarshal messages.

These advantages and the openness of the spec have inspired the creation of multiple brokers that support AMQP, including:
- [RabbitMQ][rabbitmq]
- [ActiveMQ][activemq]
- [Qpid][qpid]

## AMQP and JMS terminology

- JMS has queues and topics. A message sent on a JMS queue is consumed by no more than one client. A message sent on a JMS topic may be consumed by multiple consumers. AMQP only has queues. A message sent on an AMQP queue may reach one or more consumers.
- JMS and AMQP have an equivalent message header, providing the means to sort and route messages.
- JMS and AMQP both have brokers responsible for receiving, routing, and ultimately dispensing messages to consumers.
- AMQP has exchanges and routes. Messages are published to exchanges. Routes define on which queue(s) to publish the message.

[amqp]: http://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol
[jms]: http://en.wikipedia.org/wiki/Java_Message_Service
[amqp-spec]: http://www.amqp.org/resources/download
[pivotal]: http://gopivotal.com
[rabbitmq]: http://rabbitmq.com
[activemq]: http://activemq.apache.org/
[qpid]: http://qpid.apache.org/index.html

