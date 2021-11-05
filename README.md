# Functional Interface
- interface should have only one abstract method.
- can have multiple default methods

There are 4 Funtional Method
1. Consumer https://java2blog.com/java-8-consumer-example/
2. Predicate https://java2blog.com/java-8-predicate-examples/
3. Function
4. Supplier https://java2blog.com/java-8-supplier-example/

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

