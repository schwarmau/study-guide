# Data Stores

## CAP Theorem
It is impossible for a distributed data store to guarantee more than 2 of the following:
- Consistency: Every read gets the most recent write (or an error).
- Availability: Every request receives a non-error response.
- Partition Tolerance: The system will function regardless of time delay or dropped messages.

It is implied that a data store with network partitioning will therefore have to choose between consistency and availability.

## ACID Transactions
An ACID transaction is one which satisfies the following 4 characteristics:
- Atomicity: Each transaction, regardless of how complex, will either completely succeed or completely fail, so there are no partial updates to the data store.
- Consistency: Transactions can only bring the database from one valid state to another.
- Isolation: Transactions processed concurrently are guaranteed to have the same end result as if they were processed sequentially.
- Durability: Once a transaction has been committed it will remain committed, regardless of system availability (i.e. data is stored in non-volatile memory).

Note the difference between the "consistency" of an acid transaction and "consistency" in the CAP theorem.

## BASE Models
A data store that follows the BASE model is one which satisfies the following 3 characteristics:
- Basic Availability: The data store stays available and able to process transactions, even if some nodes/clusters/partitions have failed.
- Soft State: Consistency of data is delegated to developers instead of being handled by the database.
- Eventual Consistency: At some point, data will converge to a consistent state.

The "eventual consistency" clause need only be proven theoretically.

## Joins
Traditionally, a join is an operation that combines data from two tables in a relational database management system. In practice though, many NoSQL environments can accommodate joins in some form, even if it is not built-in functionality.

### Inner Join
**Common Syntax**: `SELECT Employee.Name, Department.Name FROM Employees AS Employee INNER JOIN Departments AS Department ON Employee.DepartmentId = Department.DepartmentId`
**Effect**: Combines rows in the Employees table with rows in the Departments table that have the same DepartmentId, ignoring nulls and rows with no match.

### Left Outer Join
**Common Syntax**: `SELECT Employee.Name, Department.Name FROM Employees AS Employee LEFT OUTER JOIN Departments AS Department ON Employee.DepartmentId = Department.DepartmentId`
**Effect**: Combines rows in the Employees table with rows in the Departments table that have the same DepartmentId. It will keep all rows in the Employees table, and if there is no matching row in the Departments table it will use null for the Department values (Department.Name in this case). It will still ignore nulls and rows with no match from the Departments table.

### Right Outer Join
**Common Syntax**: `SELECT Employee.Name, Department.Name FROM Employees AS Employee RIGHT OUTER JOIN Departments AS Department ON Employee.DepartmentId = Department.DepartmentId`
**Effect**: Combines rows in the Departments table with rows in the Employees table that have the same DepartmentId. It will keep all rows in the Departments table, and if there is no matching row in the Employees table it will use null for the Employee values (Employee.Name in this case). It will still ignore nulls and rows with no match from the Employees table. This is not a common join since it is equivalent to a Left Outer Join where the FROM and JOIN tables are swapped.

### Full Outer Join
**Common Syntax**: `SELECT Employee.Name, Department.Name FROM Employees AS Employee FULL OUTER JOIN Departments AS Department ON Employee.DepartmentId = Department.DepartmentId`
**Effect**: Produces the union of a Left Outer Join and a Right Outer Join (all rows from both tables will be accounted for, and nulls will be inserted where matches weren't found).

### Cross Join (A.K.A. Cartesian Join)
**Common Syntax**: `SELECT Employee.Name, Department.Name FROM Employees AS Employee CROSS JOIN Departments AS Department`
**Effect**: Produces the cartesian product of the two tables. A new row will be created for every combination of rows between the two tables.

## Deciding What To Use
So the lingering question is, "When do I use NoSQL, and when do I use SQL?" Well, in general, NoSQL is simply more flexible, and can be used in pretty much any situation. Most of the benefits of SQL are things that can be emulated for NoSQL within the calling code, but that does add complexity. Additionally, in the modern development environment, you can use different databases for different tasks, so keep that in mind.

Here are some things to look for that might indicate SQL being better for your use case:
- You need to accommodate a wide array of complex queries that combine results across different subdomains in your application (e.g. for generating reports).
- You need to ensure ACID compliance (e.g. for financial applications).
- You don't anticipate a lot of changes or growth.

You might instead look into using NoSQL in the following cases:
- You have budget restrictions (SQL is more expensive to scale).
- The data structures being managed are volatile/variable.
- You plan to analyze large amounts of data, but don't need to manipulate/write data in such quantities.

Other, more specific use cases for NoSQL include:
- Event capture and processing.
- Storing data for intelligence engines to use.