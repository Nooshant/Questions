 # Questions:

- Spring Boot Application Custom Exception Handling
- Multiple nodes configuration in the cloud environment for SBA deployment
- JPA filtering for data retrieval
- Database configuration in the SBA
- Serialization and Externalization in SBA
- k8s questions
- Sum of two numbers closest to zero in a Array of integers (both negative and positive numbers)
- Throwing an Custom exception from the main class and catching it in catch block 
	find the hierarchy of execution of that custom exception class
- What is Normalization in DBMS (SQL)? 1NF, 2NF, 3NF, BCNF.
- CountDownLatch
- CustomTheadPoolExecutor
- Reentrant lock
- Using multiple databases in a single transaction

https://learning.oreilly.com/videos/master-microservices-with/9781789132779/9781789132779-video6_20/

- ConcurrentHashMap working and implementation
- DeepCopy and Swallow Copy https://www.edureka.co/blog/shallow-and-deep-copy-java/
- Predicate, Consumer, Producer, Stream, Date, MetaSpace replacement of PermSpace
- GroupBy in java 8
- Static synchronized in static Synchronized ?
- Callable, Future, CountDownLatch
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

From <https://www.google.com/search?q=dependency+injection+in+spring&rlz=1C1GCEU_enIN907IN907&oq=dependency+in&aqs=chrome.1.0i433j0j0i433l2j0j69i57j69i60l2.12176j0j7&sourceid=chrome&ie=UTF-8> 

- flatMap and map in java 8
- Create a query to fetch count of employee from each city.(hint GroupBy)
- Session vs SessionFactory
- OutOfMemoryError
- What is Heap memory
- Find the common number from three array
- How to call the one microservice to another microcservices.
- How to secure the rest API
- Qualifier in spring
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
- @Qualifier use
- @Primary vs @Qualifier
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
-  What is cache and how many cache are there in hibernate? Explain when to use which one.
- Design a Branch and Bank schemas and Table. At the end, write a query to fetch all the Bank using IFSC code.
- Count equals sum from array DP problem
- Matrix related problem
- Write a program in java to compare Two employee objects (e1,e2) based on its name and age
If name is same, consider age for comparision
https://www.geeksforgeeks.org/comparator-interface-java/
	
- concurrency vs parallelism
- Create deadlock
- minorGC vs MajorGC
- How GC work
- Design MakeMyTrip database
- Design BookMyShow
- Print even and Odd using two thread.
- How recursion work
- How to reverse any number without using any datastruture
- How to select database for any application
- Diff between mongoDb and oracle

# Fidelity
	
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
	
# NETWEST

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
```

Purpose of these interfaces from oracle documentation :

Runnable interface should be implemented by any class whose instances are intended to be executed by a Thread.
The class must define a method of no arguments called run.

Callable: A task that returns a result and may throw an exception.
Implementors define a single method with no arguments called call.
The Callable interface is similar to Runnable, in that both are designed for 
classes whose instances are potentially executed by another thread. 
A Runnable, however, does not return a result and cannot throw a checked exception.

Other differences:

You can pass Runnable to create a Thread. But you can't create new Thread by passing Callable as parameter.
You can pass Callable only to ExecutorService instances.

Example:

public class HelloRunnable implements Runnable {

    public void run() {
        System.out.println("Hello from a thread!");
    }   

    public static void main(String args[]) {
        (new Thread(new HelloRunnable())).start();
    }

}
Use Runnable for fire and forget calls. Use Callable to verify the result.

Callable can be passed to invokeAll method unlike Runnable. Methods invokeAny and invokeAll perform
the most commonly useful forms of bulk execution, executing a collection of tasks and then waiting 
for at least one, or all, to complete

Trivial difference : method name to be implemented => run() for Runnable and call() for Callable.
```	
	

- How token is validated in application whether it's a valid or invalid.
- List of functional Interface
```
//Runnable
interface Runnable {
    void run();
}

//Action - throws exception
interface Action {
    void run() throws Exception;
}

//Consumer - consumes a value/values, throws exception
interface Consumer1<T> {
    void accept(T t) throws Exception;
}

//Callable - return result, throws exception
interface Callable<R> {
    R call() throws Exception;
}

//Supplier - returns result, throws exception
interface Supplier<R> {
    R get() throws Exception;
}

//Predicate - consumes a value/values, returns true or false, throws exception
interface Predicate1<T> {
    boolean test(T t) throws Exception;
}

//Function - consumes a value/values, returns result, throws exception
public interface Function1<T, R> {
    R apply(T t) throws Exception;
}

...

//Executor
public interface Executor {
    void execute(Runnable command);
}
```

- What is REST Api and difference between REST and SOAP ?
