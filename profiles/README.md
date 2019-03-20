# Understaning Spring Profiles

A Spring `ApplicationContext` can run in different profiles, defined by the user. You can use profiles to control the contents of the application depending on the environment, for instance to run a different set of beans in a test, or in a cloud platform.

Beans (with `@Bean`) or complete configuration classes (with `@Configuration`) can be marked with the [`@Profile`] annotation. For example:

```java
@Configuration
@Profile("test")
public class TestConfiguration {
   ... beans defined here
}
```

You can activate a profile at runtime by setting `spring.profiles.active` (a comma-separated list). This can be set as a System property or environment variable (`SPRING_PROFILES_ACTIVE` works too in that case), or in the case of a Spring Boot application, in `application.properties`. Spring Boot has an additional feature which is that you can append to the list of active profiles by setting `spring.profiles.include`.

By default Spring always runs in the "default" profile, but there are no other special profiles defined by Spring. Cloud Foundry runs a Spring application in the "cloud" profile.

[`@Profile`]: https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/context/annotation/Profile.html
