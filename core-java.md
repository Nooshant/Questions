# Fail-Fast

A fail-fast iterator does not allow modifications to the Collection it traverses; this means, that it will throw out ConcurrentModificationException
when such a Collection is modified while being traversed by its iterator. It is not necessary to modify and traverse the
Collection using different threads to throw this exception; it will occur even if the modification and traversal are done in the same thread.

However, there is a difference between the iterator’s remove() function and the Collection’s remove() function. 
When the iterator’s remove() is invoked, no exception is thrown. The Collection’s remove(), on the other hand, throws this exception in case of concurrent modification.

# Fail-Safe

A fail-safe iterator creates a copy of the Collection and then traverses it; this allows modification in the original Collection, 
but the changes may not be reflected during traversal. Moreover, creating a copy of a Collection is considered a waste of time and space. 
Therefore, when traversing a large Collection, fail-safe iterators can be a disadvantage.

https://www.geeksforgeeks.org/fail-fast-fail-safe-iterators-java/


# Weakhasmap

You can use a WeakHashmap to reduce the chance of a memory leak as a result of caching some object. The WeakHashMap will automatically remove
entries whenever all references to the key are removed

# Java object References types

In Java; order from strongest to weakest, there are: Strong, Soft, Weak and Phantom

- A Strong reference is a normal reference that protects the referred object from collection by GC. i.e. Never garbage collects.
- A Soft reference is eligible for collection by garbage collector, but probably won't be collected until its memory is needed. i.e. 
  garbage collects before OutOfMemoryError.
- A Weak reference is a reference that does not protect a referenced object from collection by GC. i.e. garbage collects when no Strong or Soft refs.
- A Phantom reference is a reference to an object is phantomly referenced after it has been finalized, but before its allocated memory has been reclaimed.

Source

Analogy: Assume a JVM is a kingdom, Object is a king of the kingdom, and GC is an attacker of the kingdom who tries to kill the king(object).

- When King is Strong, GC can not kill him.
- When King is Soft, GC attacks him but King rule the kingdom with protection until resource are available.
- When King is Weak, GC attacks him but rule the kingdom without protection.
- When king is Phantom, GC already killed him but king is available via his soul.

# BigDecimal
  https://www.geeksforgeeks.org/bigdecimal-class-java/

# Need of wrapper class
  https://www.geeksforgeeks.org/need-of-wrapper-classes-in-java/
 
# Comparator and Comparable in PriorityQueue

```
package thakur.compar.pqueue;

import java.time.LocalDate;
import java.util.Comparator;
import java.util.PriorityQueue;

class Employee  { //implements Comparable<Employee>
	 
    private Long id;
    private String name;
    private LocalDate dob;
 
    public Employee(Long id, String name, LocalDate dob) {
        super();
        this.id = id;
        this.name = name;
        this.dob = dob;
    }
	public Long getId() {
		return id;
	}
	public void setId(Long id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public LocalDate getDob() {
		return dob;
	}
	public void setDob(LocalDate dob) {
		this.dob = dob;
	}

	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + ", dob=" + dob + "]";
	}
}
```

```
class EmployeeNameComparator implements Comparator<Employee>
{
	@Override
	public int compare(Employee o1, Employee o2) {
		
		if(o1.getName().hashCode() > o2.getName().hashCode())
		{
			return -1;
		}
		else if (o1.getName().hashCode() < o2.getName().hashCode()) {
			return 1;
		}
		else {
			return 0;
		}
	}
}
```

```
public class PriorityQueueDemo {
	
	public static void main(String[] args) {
		
		Comparator<Employee> nameSorter = Comparator.comparing(Employee::getName);//ascending order
		
		//PriorityQueue<Employee> priorityQueue = new PriorityQueue<>(new EmployeeNameComparator()); // descending order
		PriorityQueue<Employee> priorityQueue = new PriorityQueue<>(nameSorter);
        
		priorityQueue.add(new Employee(1l, "AAA", LocalDate.now()));
		priorityQueue.add(new Employee(4l, "CCC", LocalDate.now()));
		priorityQueue.add(new Employee(5l, "BBB", LocalDate.now()));
		priorityQueue.add(new Employee(2l, "FFF", LocalDate.now()));
		priorityQueue.add(new Employee(3l, "DDD", LocalDate.now()));
		priorityQueue.add(new Employee(6l, "EEE", LocalDate.now()));
		 
		while(true) 
		{
		    Employee e = priorityQueue.poll();
		    System.out.println(e);
		     
		    if(e == null) break;
		}		
	}
}
```


Employee class must be comparable either using COMPARATOR or COMPARABLE otherwise classCastException because Employee class is not comparable by default.

# ENUM use ?

Use static final constants when you want to define a **singular** constant value.
```
public class PhysicsConstants{ 
    public static final float GRAVITY = 9.81f; 
} 
```
In this case the only possible value for the gravity in this application would be the earth gravity.
Suppose you want to allow several values for gravity, use an enum:

```
public enum Gravity { 
 
    Earth(9.81f), Mars(3.8f), Moon(1.622f); 
    private float gravity; 
 
    private Gravity(float gravity) { 
        this.gravity = gravity; 
    } 
 
    public float getGravity() { 
        return gravity; 
    } 
} 
```
- Enum constructor must be always private
- Enums can implement any interface and override methods
- Enum in java implicitly implement both Serializable and Comparable interface
- Abstact methods can be implemented in Enums can provide different implementations for different Enum constants
- We can create a list directly from the Enum constants using the values() method

# Runnable Vs Callable
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

	- Comparator using Java-7 and Java-8
	
```
/**** Anonymous Class (Old Way) ****/
        Comparator<Employee> comparator1 = new Comparator<Employee>() {
            @Override
            public int compare(Employee emp1, Employee emp2) {
                return new Integer(emp1.getAge()).compareTo(new Integer(emp2.getAge()));
            }
        };
 
        /*** Sorting the Employee List Using Comparator By Age ****/
        Collections.sort(employeeList1, comparator1);
        System.out.println("-------------After Sorting list Using Anonymous Class-------------");
        System.out.println(employeeList1);
 
        List<Employee> employeeList2 = getEmployees();
 
        /**** Lambda Expression from Java8 ****/
        Comparator<Employee> comparator2 = (emp1, emp2) -> {
            return new Integer(emp1.getAge()).compareTo(new Integer(emp2.getAge()));
        };
 
        /*** Sorting the Employee List Using Comparator By Age ****/
        Collections.sort(employeeList2, comparator2);
        System.out.println("---------------After Sorting List Using Lambda Expression From Java8--------------");
        System.out.println(employeeList2);
```
https://techvidvan.com/tutorials/java-interview-questions-for-experienced/
	
![image](https://user-images.githubusercontent.com/29571875/133917442-bda8a3e9-adf3-4847-8405-aba58e9acf51.png)
	
# Race Condition

>A race condition occurs when two or more threads can access shared data and they try to change it at the same time. Because the thread scheduling algorithm can swap between threads at any time, you don't know the order in which the threads will attempt to access the shared data. Therefore, the result of the change in data is dependent on the thread scheduling algorithm, i.e. both threads are "racing" to access/change the data.
Problems often occur when one thread does a "check-then-act" (e.g. "check" if the value is X, then "act" to do something that depends on the value being X) and another thread does something to the value in between the "check" and the "act".



