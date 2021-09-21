# LINKS
- https://java2blog.com/spring-interview-questions-and-answers/

- https://java2blog.com/hibernate-interview-questions-and-answers/

- https://www.geeksforgeeks.org/java-singleton-design-pattern-practices-examples/
- https://www.journaldev.com/1377/java-singleton-design-pattern-best-practices-examples  (BEST)
- https://www.interviewbit.com/hibernate-interview-questions/ (Hibernate)

# Questions:

- Spring Boot Application Custom Exception Handling
  
```
@ControllerAdvice
@RestController
public class CustomizedResponseEntityExceptionHandler extends ResponseEntityExceptionHandler {
	
	
	@ExceptionHandler(Exception.class)
	public final ResponseEntity<Object> handleAllException(Exception ex, WebRequest request) {
		ExceptionResponse response = new ExceptionResponse(new Date(), ex.getMessage(), request.getDescription(false));
		return new ResponseEntity<Object>(response, HttpStatus.INTERNAL_SERVER_ERROR);
	}

	@ExceptionHandler(UserNotFoundException.class)
	public final ResponseEntity<Object> handleUserNotFoundException(UserNotFoundException ex, WebRequest request) {
		ExceptionResponse response = new ExceptionResponse(new Date(), ex.getMessage(), request.getDescription(false));
		return new ResponseEntity<Object>(response, HttpStatus.NOT_FOUND);
	}
}
// ExceptionResponse is custom model class
public class ExceptionResponse {
	private Date timestamp;
	private String message;
	private String details;
}
```

- Multiple nodes configuration in the cloud environment for SBA deployment
- JPA filtering for data retrieval
- Database configuration in the SBA
- Serialization and Externalization in SBA
- k8s questions
- Sum of two numbers closest to zero in a Array of integers (both negative and positive numbers)
- Throwing an Custom exception from the main class and catching it in catch block 
	find the hierarchy of execution of that custom exception class
- What is Normalization in DBMS (SQL)? 1NF, 2NF, 3NF, BCNF.

- ReentrantLock key features as per this article

> Ability to lock interruptibly.
Ability to timeout while waiting for lock.
Power to create fair lock.
API to get list of waiting thread for lock.
Flexibility to try for lock without blocking.

- Using multiple databases in a single transaction

https://learning.oreilly.com/videos/master-microservices-with/9781789132779/9781789132779-video6_20/

- DeepCopy and Swallow Copy https://www.edureka.co/blog/shallow-and-deep-copy-java/
- Predicate, Consumer, Producer, Stream, Date, MetaSpace replacement of PermSpace
- GroupBy in java 8
  ```
  		List < Employee > employees = Arrays.asList(
				   new Employee(1, 10, "Chandra"), new Employee(1, 20, "Rajesh"),
				   new Employee(1, 30, "Rahul"), new Employee(1, 20, "Ramana"),  new Employee(1, 25, "Ramana"));
		
		
		Map<Integer, List<Employee>> groupByname = employees.stream().collect(Collectors.groupingBy(Employee::getDepartment));
  ```
  
- Static synchronized in static Synchronized ?
 ```
 class Sample
{
	public static void m1() {
		synchronized (Sample.class) {
			System.out.println("m1.... "+Thread.currentThread().getName());
			m2();
		}
	}

	public static void m2() {
		synchronized (Sample.class) {
			System.out.println("m2.... "+Thread.currentThread().getName());
		}
	}
}


public class NestedStaticSyncDemo {
	public static void main(String[] args) {
		
		new Thread(()->{
			Sample.m1();
		}).start();
		
		new Thread(()->{
			Sample.m1();
		}).start();
		
	}
}
 ```
- Callable, Future, CountDownLatch https://www.geeksforgeeks.org/callable-future-java/ 
- How to make a class immutable  which have Employee and Address class as attribute.
```
public class Employee{
    private int id;
    private Address address;
```
From <https://stackoverflow.com/questions/34109363/how-can-we-maintain-immutability-of-a-class-with-a-mutable-reference> 

- Object level and Class level locks in Java

From <https://www.geeksforgeeks.org/object-level-class-level-lock-java/> 

- ThreadpoolExecutor and CachedThreadPool

From <https://stackoverflow.com/questions/17957382/fixedthreadpool-vs-cachedthreadpool-the-lesser-of-two-evils> 
https://stackoverflow.com/questions/3718148/java-class-level-lock-vs-object-level-lock
- How to set an ideal thread pool size

From <https://engineering.zalando.com/posts/2019/04/how-to-set-an-ideal-thread-pool-size.html> 

Number of threads = Number of Available Cores * Target CPU utilization * (1 + Wait time / Service time)

From <https://engineering.zalando.com/posts/2019/04/how-to-set-an-ideal-thread-pool-size.html> 

- What are the different types of dependency injection in Spring?
https://jstobigdata.com/spring/inversion-of-control-and-dependency-injection-in-spring/

- flatMap and map in java 8
- Create a query to fetch count of employee from each city.(hint GroupBy)
- Session vs SessionFactory
- OutOfMemoryError
- What is Heap memory
- Find the common number from three array
- How to call the one microservice to another microcservices.
- How to secure the rest API
- Qualifier in spring https://jstobigdata.com/spring/fine-tune-auto-wiring-using-primary-and-qualifier/
- FuntionalInterface with example
- Default method in FunctionalInterface
- @configuration  https://stackoverflow.com/questions/24014919/understanding-spring-configuration-class
https://stackoverflow.com/questions/5113579/how-to-import-spring-config-xml-of-one-project-into-spring-config-xml-of-another



Constructor argument resolution

```
package x.y;
public class Foo {
public Foo(Bar bar, Baz baz) {
      // ...
  }
}

<beans>
  <bean id="foo" class="x.y.Foo">
      <constructor-arg ref="bar"/>
      <constructor-arg ref="baz"/>
  </bean>
<bean id="bar" class="x.y.Bar"/>
  <bean id="baz" class="x.y.Baz"/>
</beans>
```

https://docs.spring.io/spring-framework/docs/3.0.x/spring-framework-reference/html/beans.html#beans-factory-xml-import (bean import example)

- How application talk to database
- List<Object> list = new ArrayList<String>();   ???? Possible and does it follow inheritance
- Bank have many Branch (find all the branch using IFSC id) and how to design the table and Entity class
- What is your project means NFVD ?
- String s ="abc"; s.concat("def"); sop(s).   What is happening over here.
- Annotation in JPA
- Difference in JPA and Hibernate
	
	![image](https://user-images.githubusercontent.com/29571875/133926003-a77d874f-cda0-4e2c-8c78-ca7e1840e841.png)

- @Qualifier use
- @Primary vs @Qualifier https://jstobigdata.com/spring/fine-tune-auto-wiring-using-primary-and-qualifier/
- Use of hashcode and equals method
- Atomicity and .. In sql
- All the mapping name in JPA
- @manytomany example to use of it.
- Primary key , foreign key and composite key (how many primary key can be in a table)
- Second largest element in an array
- Permutation of an array
- Reflection API
- What is the significance of serialization and deserialization
- Common problem in Serialization
- Deadlock and Race Condition
- How to create Schemas
- What is cache and how many cache are there in hibernate? Explain when to use which one.
- Design a Branch and Bank schemas and Table. At the end, write a query to fetch all the Bank using IFSC code.
- Count equals sum from array DP problem
- Matrix related problem
- Write a program in java to compare Two employee objects (e1,e2) based on its name and age
If name is same, consider age for comparision
https://www.geeksforgeeks.org/comparator-interface-java/
	
- concurrency vs parallelism
- Create deadlock
- minorGC vs MajorGC  https://dzone.com/articles/minor-gc-vs-major-gc-vs-full
- How GC work   https://stackify.com/what-is-java-garbage-collection/ https://www.betsol.com/blog/java-memory-management-for-java-virtual-machine-jvm/
- Design MakeMyTrip database
- Design BookMyShow
- Print even and Odd using two thread.
- How recursion work
- How to reverse any number without using any datastruture
- How to select database for any application
- Diff between mongoDb and oracle

# F...y
	
- How does application store user login
- What is the token and (who)how does application generate it.
- How to deploy the Microservices.
- What is require dependency to start the microservices.
- richardson api maturity model
- Hateos concept
- Apart from first Level cache and second, can we use other cache.
- What is the need of microservices.
- What is lambda ?
- How many cache ? and Can we have external cache ?
	
# N...T

- Callable vs Throwable
- what is BigDecimal
- What is difference between Spring and Springboot
- How springboot work internally.
- How parent maven is inherited by all the sub-Child maven.
- ConcurrentModification exception and in build collection for that.
- Fail-fast and fail-safe
- How to prevent ConcurrentModificationException
- Wrapper class and need of it.
- what to use int or Integer while declaring the variable
- What is the need and what is String constant pool
- String str = new String("abc"); How many object will be created
- WeakHashMap when to use
- Weak reference and ... reference ?
- What is the need of ENUM.
- Singleton class and Immutable class
- What is reentrant Lock.
- When to use Runnable and Callable.
- What is REST Api and difference between REST and SOAP ?
	![image](https://user-images.githubusercontent.com/29571875/131291504-ac37c1e2-08e6-46ac-b8eb-398a407663fd.png)
	
	Request itself provide information about business logic
	Standard response code for each call.
	
	
	![image](https://user-images.githubusercontent.com/29571875/131291803-08a2cae3-97fd-4be8-8889-25d3bf647a21.png)
	It is more secure than REST since whole envelope is encrypted.
	It has custom type of response code, means developer has to decide.

- Min no. of swaps to sort the array
- Create Deadlock in java
- Jboss folder structure
	https://github.com/Nooshant/README-IQ/blob/main/sampleCode.md#jboss-folder-structure
- How to do packaging using jboss
- Log4j configuration  https://mail.codejava.net/coding/how-to-configure-log4j-as-logging-mechanism-in-java
	![Untitled](https://user-images.githubusercontent.com/29571875/133925861-6e49c2de-522b-42cf-850f-5af295c787ed.png)

- Print Alphabet and number using two thread. a1b2c3d4......
- Springboot support which all embedded server ?
	- Spring Boot supports Tomcat, Undertow, and Jetty as embedded servers.
- What Is a Spring Context?
```
Spring contexts are also called Spring IoC containers, which are responsible for instantiating, configuring, and assembling beans by reading 
configuration metadata from XML, Java annotations, and/or Java code in the configuration files.
```

- how to design microservices and before implementation
- What is Atomic in Thread.
- What is ThreadLocal?  https://www.geeksforgeeks.org/java-lang-threadlocal-class-java/
- ConcurrentHashMap working like how many write operation can be performed parallel. https://itsromiljain.medium.com/curious-case-of-concurrenthashmap-90249632d335
- ReentrantWriteLock and ReentrantReadLock how does it work have sample code to see is there any problem in that.
	- https://github.com/Nooshant/README-IQ/blob/main/sampleCode.md
- what is newCachedThreadPool() and what will happen if it has created 10 more thread based on load and when the load decreases what happens with this thread.
  > Creates a thread pool that creates new threads as needed, but will reuse previously constructed threads when they are available. These pools will typically improve the performance of programs that execute many short-lived asynchronous tasks. Calls to execute will reuse previously constructed threads if available. If no existing thread is available, a new thread will be created and added to the pool. Threads that have not been used for sixty seconds are terminated and removed from the cache. Thus, a pool that remains idle for long enough will not consume any resources. Note that pools with similar properties but different details (for example, timeout parameters) may be created using ThreadPoolExecutor constructors. If all allocated threads are occupied while a new task comes in, then it creates a new thread, as offering a new task to a SynchronousQueue always fails when there is no one on the other end to accept it!

```	
public static ExecutorService newCachedThreadPool() {
    return new ThreadPoolExecutor(0, Integer.MAX_VALUE,
                                  60L, TimeUnit.SECONDS,
                                  new SynchronousQueue<Runnable>());
}
```
	
- Creational Design pattern  
   - Factory pattern https://adnjavainterview.blogspot.com/2015/07/factory-design-pattern-in-java.html
   - Abstract Factory Pattern
   - Singleton
   - Builder 
- create a singleton using Enum have two method, show the implementation 
- How to create Immutable class have two class Employee and it has Address as another field as object. http://adnjavainterview.blogspot.com/2019/06/how-to-create-custom-immutable-class-with-mutable-object-reference-injava.html
- what will happen if the loading jar size during runtime is larger than Metaspace(considering the max of RAM size)
- Shutdown vs ShutdownNow method difference
	```
	shutdown() initiates an orderly shutdown in which previously submitted tasks are executed, but no new tasks will be accepted. 
	... shutdownNow() attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns
	a list of the tasks that were awaiting execution.
	```
- Optional in Java-8
- Requirement
     - Have 5 doors and single key for all these door.
     - Many people has to open the door waiting
     - It may be chance that one could take the key to open door and took more time.
     - How would you handle that people waiting for key should not wait for long.
     - Design this requirement.
- what is race condition, why does it occur. How can you handle it. https://github.com/Nooshant/README-IQ/blob/main/core-java.md#race-condition
- How to find the issue that it is cause of race Condition
- How to create thread dump and verify in log that it has because of race condition.
- How to detect deadlock in java and how to prevent ?  https://dzone.com/articles/how-analyze-java-thread-dumps
- What is WSDL in SOAP ? https://www.guru99.com/wsdl-web-services-description-language.html
- What is namespace in xml schema ? https://www.informit.com/articles/article.aspx?p=169106&seqNum=2
- What is .xsd and what is the use of it ? https://study.com/academy/lesson/what-is-xsd-examples-tutorial.html
- Builder Design pattern? http://adnjavainterview.blogspot.com/2019/05/builder-design-pattern-in-java.html
    In realtime it is used in StringBuilder and StringBuffer in java.

 - Hibernate one to one mapping using annotation ?
      http://adnjavainterview.blogspot.com/2018/03/hibernate-one-to-one-mapping-example.html
	
- Name the idempotent method of Webservices operation from eg. PUT,DELETE,GET,...
  > Except POST method all are Idempotent.

- why POST method is not idempotent ?
> HTTP POST. Generally – not necessarily – POST APIs are used to create a new resource on server. So when you invoke the same POST request N times, you will have N new resources on the server. So, POST is not idempotent.
