# Understanding Application Context

The [`ApplicationContext`] is the central interface within a Spring application for providing configuration information to the application. It is read-only at run time, but can be reloaded if necessary and supported by the application. A number of classes implement the `ApplicationContext` interface, allowing for a variety of configuration options and types of applications.

The `ApplicationContext` provides:

 - Bean factory methods for accessing application components.
 - The ability to load file resources in a generic fashion.
 - The ability to publish events to registered listeners.
 - The ability to resolve messages to support internationalization.
 - Inheritance from a parent context.

 > **NOTE**: This understanding guide provides details about Spring's usage of the application context. But in most situations, developers do NOT need to directly access the application context.

## Access the application context

There are a few methods for obtaining a reference to the application context. You can implement [`ApplicationContextAware`] as in the following example:

```java
package hello;

import org.springframework.beans.BeansException;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;

public class A implements ApplicationContextAware {

    private ApplicationContext applicationContext;

    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        this.applicationContext = applicationContext;
    }

}
```

There are other options like field injection, but that technique is [best avoided](http://olivergierke.de/2013/11/why-field-injection-is-evil/) due to issues that may arise.

Before using the application context to find beans, there are better techniques to use first.

```java
@SpringBootApplication
public class Application {

	@Bean
	RedisMessageListenerContainer container(RedisConnectionFactory connectionFactory,
			MessageListenerAdapter listenerAdapter) {

		RedisMessageListenerContainer container = new RedisMessageListenerContainer();
		container.setConnectionFactory(connectionFactory);
		container.addMessageListener(listenerAdapter, new PatternTopic("chat"));

		return container;
	}
	...
}
```

In the code above, there are two arguments to the bean definition: `RedisConnectionFactory` and `MessageListenerAdapter`. The method expresses its needs and Spring's DI container will supply them assuming they are available. While it's possible to fetch these beans directly the an instance of `ApplicationContext`, such a solution leans too heavily on container APIs and is not necessary.

[`ApplicationContext`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/context/ApplicationContext.html
[`ApplicationContextAware`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/context/ApplicationContextAware.html
[`@Autowired`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/beans/factory/annotation/Autowired.html