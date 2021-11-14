# INDEX

- An index is performance tuning method of allowing faster retrieval of records from the table. An index creates an entry for
  each value and it will be faster to retrieve data.
  
 - https://www.guru99.com/sql-interview-questions-answers.html

- While it (mostly) speeds up a `select`, it slows down `inserts`, `updates` and `delete` because the database engine does
  not have to write the data only, but the index, too. An index need space on hard disk (and much more important) in RAM

# What is the ACID property in a database?

ACID stands for Atomicity, Consistency, Isolation, Durability. It is used to ensure that the data transactions are processed reliably in a database system. 

- Atomicity:  It means if one part of any transaction fails, the entire transaction fails and the database state is left unchanged.
- Consistency:  your transaction never leaves the database without completing its state.
- Isolation: The main goal of isolation is concurrency control.
- Durability: Durability means that if a transaction has been committed, it will occur whatever may come in between such as power loss, crash or any sort of error.


 # Write SQL query to find the 3rd highest salary from a table without using the TOP/limit keyword.**

```
 SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 = (
                SELECT COUNT( DISTINCT ( Emp2.Salary ) )
                FROM EmployeeSalary Emp2
                WHERE Emp2.Salary > Emp1.Salary
            )
 ```
 
 For more info... https://www.geeksforgeeks.org/sql-query-to-find-second-largest-salary/
 
 # Composite Key vs Candidate key 
 
**Candidate Key**: A nominee for primary key field is known as candidate key.

**Composite Key**: Creating more than one primary key is jointly known as composite key.

Update : A candidate key is a unique key that can be used as a primary key. Composite key is a key of two or more attributes that uniquely identifies the row. A key is a set of columns that can be used to uniquely identify each row within a table
 
 # Primary vs Unique key
 
- Primary key will not accept NULL values whereas Unique key can accept NULL values.
- A table can have only one primary key whereas there can be multiple unique key on a table.
 
