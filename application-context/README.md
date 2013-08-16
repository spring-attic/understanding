# Understanding Application Context

The [`ApplicationContext`] is the central interface within a Spring application for providing configuration information to the application. It is read-only at run time, but can be reloaded if necessary and supported by the application. A number of classes implement the `ApplicationContext` interface, allowing for a variety of configuration options and types of applications.

The `ApplicationContext` provides:

 - Bean factory methods for accessing application components.
 - The ability to load file resources in a generic fashion.
 - The ability to publish events to registered listeners.
 - The ability to resolve messages to support internationalization.
 - Inheritance from a parent context.

## Access the application context

There are a few methods for obtaining a reference to the application context. You can implement [`ApplicationContextAware`] as in the following example:

```java
package hello;

import org.springframework.beans.BeansException;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;

public class A implements ApplicationContextAware {

    private ApplicationContext applicationContext;

    public void setApplicationContext(ApplicationContext applicationContext) {
        this.applicationContext = applicationContext;
    }

}
```

You can also use the [`@Autowired`] annotation to inject a reference directly into your class:

```java
package hello;
 
import org.springframework.beans.factory.annotation.Autowired;
 
public class B {

    @Autowired private ApplicationContext applicationContext;

}
```


[`ApplicationContext`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/context/ApplicationContext.html
[`ApplicationContextAware`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/context/ApplicationContextAware.html
[`@Autowired`]: http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/beans/factory/annotation/Autowired.html