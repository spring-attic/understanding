# Understanding POJOs

POJO means **Plain Old Java Object**. It refers to a Java object (instance of definition) that isn't bogged down by framework extensions.

For example, to receive messages from JMS, you need to write a class that implements the `MessageListener` interface. 

```java
public class ExampleListener implements MessageListener {

    public void onMessage(Message message) {
        if (message instanceof TextMessage) {
            try {
                System.out.println(((TextMessage) message).getText());
            }
            catch (JMSException ex) {
                throw new RuntimeException(ex);
            }
        }
        else {
            throw new IllegalArgumentException("Message must be of type TextMessage");
        }
    }

}
```

This ties your code to a particular solution (JMS in this example) and makes it hard to later migrate to an alternative messaging solution. If you build your application with lots of listeners, choosing AMQP or something else can become hard or impossible based on biting off this much technical debt.

A POJO-driven approach means writing your message handling solution free of interfaces.

```java
@Component
public class ExampleListener {

    @JmsListener(destination = "myDestination")
    public void processOrder(String message) {
    	System.out.println(message);
    }
}
```

In this example, your code isn't directly tied to any interface. Instead, the responsibility of connecting it to a JMS queue is moved into annotations, which are easier to update. In this specific example, you could replace `@JmsListener` with `@RabbitListener`.

This is just one example, but is not meant to illustrate JMS vs. RabbitMQ, but instead the value of coding without being tied to specific interfaces. By using **plain old Java objects**, your code is much more simplified, which lends to better testing, flexibility, and ability to change technical decisions at future stages based on knowledge and shifting requirements.

The Spring Framework and its various portfolio projects are always aiming for ways to reduce coupling between your code and existing libraries. This is a principle concept of dependency injection, where the way your service is utilized should be part of wiring the application and not the service itself.