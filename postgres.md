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
