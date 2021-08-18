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
