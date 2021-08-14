# Spring vs SpringBoot

Benefits of Spring Boot
-    Spring Boot doesn’t require you to deploy WAR files.

-    It creates stand-alone applications.
-    It helps embed Tomcat, Jetty, or Undertow directly.
-    It doesn’t require XML configuration.
-    It aims to reduce the LOC.
-    It offers production ready features.
-    It is easier to launch.
-    Easier customization and management.

 The Spring framework can be used for all layers of implementation in the development of an application.

-    Considering its POJO model, it is a very lightweight framework.
-    It allows loose coupling and easy testability.
-    It supports declarative programming.
-    It is capable of eliminating the formation of singleton and factory classes.
-    It supports both XML and annotation configurations.
-    It provides middleware services.


# Using the @SpringBootApplication Annotation

@SpringBootApplication annotation can be used to enable those three features, that is:

``@EnableAutoConfiguration:`` enable Spring Boot’s auto-configuration mechanism

``@ComponentScan:`` enable @Component scan on the package where the application is located (see the best practices)

``@Configuration:`` allow to register extra beans in the context or import additional configuration classes


Disabling Specific Auto-configuration Classes
```
@Configuration
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
public class MyConfiguration {
}
```


# How Springboot work internally ?
- https://gainjavaknowledge.medium.com/how-spring-boot-application-works-internally-dd9bd3ecc487


# How springboot auto-configuratuon works ?
-  https://www.javadevjournal.com/spring-boot/how-spring-boot-auto-configuration-works/
