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

# Spring

6. What is Auto Wiring?

No
This option is default for spring framework and it means that autowiring is OFF. You have to explicitly set the dependencies using <property> tags in bean definitions.

byName
This option enables the dependency injection based on bean names. When autowiring a property in a bean, the property name is used for searching a matching bean definition in the configuration file. If such a bean is found, it is injected into the property. If no such bean is found, an error is raised.

byType
This option enables the dependency injection based on bean types. When autowiring a property in bean, the property’s class type is used for searching a matching bean definition in the configuration file. If such a bean is found, it is injected into the property. If no such bean is found, an error is raised.

 constructor
Autowiring by constructor is similar to byType, but applies to constructor arguments. In autowire enabled bean, it will look for class type of constructor arguments, and then do a autowire bytype on all constructor arguments. Please note that if there isn’t exactly one bean of the constructor argument type in the container, a fatal error is raised.

7. What are the important roles of an IOC Container?
 
The Spring IoC container is at the core of the Spring Framework. The container will create the objects, wire them together, configure them, and manage their complete life cycle from creation till destruction. The Spring container uses dependency injection (DI) to manage the components that make up an application.

8. What are Bean Factory and Application Context?
 
A BeanFactory is essentially nothing more than the interface.
The BeanFactory enables us to read bean definitions and access them using the bean factory.

The ApplicationContext container includes all functionality of the BeanFactory container, so it is generally recommended over the BeanFactory. ClassPathXmlApplicationContext  FileSystemXmlApplicationContext and WebXmlApplicationContext

9. Can you compare Bean Factory with Application Context?

10. How do you create an application context with Spring?
 
ApplicationContext context = new FileSystemXmlApplicationContext
         ("C:/Users/ZARA/workspace/HelloSpring/src/Beans.xml");
      
      HelloWorld obj = (HelloWorld) context.getBean("helloWorld");
      obj.getMessage();

11. How does Spring know where to search for Components or Beans?
 
@ComponentScan
Spring is a dependency injection framework. It is all about beans and wiring in dependencies.
The first step of defining Spring Beans is by adding the right annotation — @Component or @Service or @Repository.
In SpringBoot @SpringBootApplication notation has already this annotation.
<context:component-scan base-package="com.in28minutes" />

12. Spring @Component, @Service, @Repository, @Controller Difference ?
 
Spring @Component, @Service, @Repository and @Controller annotations are used for automatic bean detection using 
classpath scan in Spring framework. @Component is a generic annotation. Difference of @Service, @Repository, @Controller
 with @Component is they are special cases of @Component and used for particular purposes. The difference is just classification only.
 
13. What is the default scope of a bean?
Singleton is the default scope for a Bean, the one that will be used if nothing else is indicated. This scope implies that Spring container will create an only shared instance of the class designated by this bean, so each time the Bean is required the same object will be injected.

14. Are Spring beans thread safe?
 
No

15. What are the other scopes available?
 
singleton.
prototype.
request.
session.
application.
websocket.

16. What are the different types of dependency injections?
 
There are three types of dependency injection — constructor injection, method injection, and property injection

18. What is auto-configuration in SB ?
 
Spring Boot auto-configuration attempts to automatically configure your Spring application based on the jar dependencies that you have added. For example, If HSQLDB is on your classpath, and you have not manually configured any database connection beans, then we will auto-configure an in-memory database.

19. How do you implement Exception Handling for RESTFul Web Services?
 
https://www.java4s.com/web-services/exception-handling-in-restful-web-services-jax-rs-with-jersey/

You need to opt-in to auto-configuration by adding the @EnableAutoConfiguration or @SpringBootApplication annotations to one of your @Configuration classes.

# Spring MVC

All the annotation in MVC
![image](https://user-images.githubusercontent.com/29571875/138545223-2c4693cc-e279-4a6b-89a7-5a5331adbe1f.png)

