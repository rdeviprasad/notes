# What are Databases?
Database is used to store and retrieve data.
## Can Database be used as a server?
It can be but not recommended
## Is Database a file system?
it is file system which is structured well for CRUD on data.
## Can database in memory?
It can be. But the expectation is to have data for a long period of time.
## Are databases a single source of truth (consistent & available)?
Usually the databases are expected to be consistent. But in some cases it is okay for the database to be inconsistent - like number of likes on a post.
Also databases are expected to be available for user requests always.
## What is a Database Management System (DBMS)?
A DBMS:
* Decides how and where any data is to be kept
* Manages configurations when storing the data
* Helps with read replicas and coordination in the system

# Storage and Retrieval
## How databases store data?
There are multiple hardwares that can be used like magnetic tapes and hard disks
## What algorithms are used in storing data?
* In relational DB -> B+ Trees (or log structured merge trees) are used which create indexes of the data.
* Pages
* Hashtables
* Pointers
## How do databases read data?
Hash Tables + B+ Trees create indexes

Tables - Structured data stores having columns of different data types like String, Integer, Date, etc.
Tables are built on top of indexes (B+ Trees), Fast lookups (hash tables), Foreign keys (pointers).

### Example Query
``` SQL
select * from profiles where first_name = "john" group by date_of_birth having count > 100 order by country limit 100;
```
Here:
* `from profiles` - tells where to read from
* `where first_name = "john"` - tells which rows to read
* `group by date_of_birth` - tells how to cluster the data
* `having count > 100` - tells which aggregations to apply
* `order by country` - tells the order in which the result should be returned
* `limit 100` - tells how many rows to return

### Query Optimizer
Users do not know how the data is structured internally. So the job of query optimizer is to take the user query and create a plan, based on heuristics, to execute the query in an optimized way to improve performance.

# What is a NoSQL Database?
Any database which do not support relational queries is put under a common term called NoSQL databases. Most common structure for these databases is a key-value store (document oriented database). They can be imagined as a persistent hashmap.

# Types of Databases
## What is a Graph database?
* Stores data internally as nodes and edges
* Used to perform graph queries efficiently
## What is a time-series database?
* Stores records that are part of time-series
* Aggregate and compress time-stamped data
* Used to store metrics, instrumentation data
* Few time-series db are written on top of relational db
## What is an object oriented database?
* Designed to work with complex data objects
* Are usually implemented using relational DB
# How to choose a database?
* The type of application you are building
* The type of database where you have a deeper knowledge
* The tradeoffs that a database gives you

### Example
* Postgres has high consistency and high durability. But in terms of availability, it needs to be improved. If a node goes down in postgres, better to have a read replica to take its place.
* Cassandra has a high availability due to its cluster. Fault tolerance is inbuilt. But it is not highly consistent. It needs to be tuned for consistency.

