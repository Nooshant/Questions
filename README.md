# Functional Interface
- interface should have only one abstract method.
- can have multiple default methods

There are 4 Funtional Method
1. Consumer
2. Predicate
3. Function
4. Supplier

Extention of functional Method

1. Consumer - BiConsumer
2. Predicate – BiPredicate
3. Function – BiFunction, UnaryOperator, BinaryOperator

- CONSUMER
 The consumer interface accepts one argument but there is no return value.
  The name of function inside this interface is `accept`
  
  https://dzone.com/articles/functional-interface-explained-in-detail-introduce
 

# Default Method
- The default method has been introduced in interface so that a new method can be appended in the
  class without affecting the implementing class of the existing interfaces.
  
  
  
  # FlatMap 
  
  You saw how to return the length for each word in a list using the method map. Let’s extend this idea a bit further: 
  how could you return a list of all the unique characters for a list of words? For example, given the list of 
  words ["Hello", "World"] you’d like to return the list ["H", "e", "l", "o", "W", "r", "d"].

You might think that this is easy, that you can just map each word into a list of characters
and then call distinct to filter duplicate characters. A first go could be like this:

```
words.stream()
     .map(word -> word.split(""))
     .distinct()
     .collect(toList());
```

The problem with this approach is that the lambda passed to the map method returns a String[] (an array of String) for each word.
So the stream returned by the map method is actually of type Stream<String[]>.
What you really want is Stream<String> to represent a stream of characters. Answer would ``helloworld``

Solution for above is, first convert stream of stream(Hello and World are different stream)

```
words.stream()
     .map(word -> word.split(""))
     .flatMap(Arrays::stream)
     .distinct()
     .collect(toList());
```

# SQL
 
**1.What is the ACID property in a database?**
The full form of ACID is Atomicity, Consistency, Isolation, and Durability. To check the reliability of the transactions, ACID properties are used.

- Atomicity refers to completed or failed transactions, where transaction refers to a single logical operation on data. This implies that if any 
 aspect of a transaction fails, the whole transaction fails and the database state remains unchanged.
- Consistency means that the data meets all of the validity guidelines. The transaction never leaves the database without finishing its state.
- Concurrency management is the primary objective of isolation.
- Durability ensures that once a transaction is committed, it will occur regardless of what happens in between, such as a power outage, a fire, 
 or some other kind of disturbance.
 
 
 **2. Write SQL query to find the 3rd highest salary from a table without using the TOP/limit keyword.**

```
 SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 = (
                SELECT COUNT( DISTINCT ( Emp2.Salary ) )
                FROM EmployeeSalary Emp2
                WHERE Emp2.Salary > Emp1.Salary
            )
 ```
 
 
 


