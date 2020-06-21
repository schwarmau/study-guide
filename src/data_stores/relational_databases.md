# Relational Databases

Relational data stores are the ones most people are comfortable with. They can be categorized by the following:
- Data is stored as relationships, in tabular form, usually representing an entity type.
- Robust support for joins.
- Requirement of ACID transactions.
- Out-of-the-box support for relational algebra (including aforementioned joins).

A core aspect of designing relational databases is the normalization of data. That is: The process of structuring a relational database to reduce redundancies in the data and improve data integrity. Normalization is an incremental process, and the varying degrees of normalization are as follows:
1. 1NF (First Normal Form): Each column of a table must be atomic (contain non-separable values, such as strings, integers, and dates, but not lists). To achieve this, you can usually split the non-atomic columns into their own tables and use a key to relate them to the original table.
2. 2NF (Second Normal Form): Each non-key attribute (column) must be dependent on the whole table key (not just part of it). To achieve this, you can usually move a part of the key and its dependencies to a new table.
3. 3NF (Third Normal Form): Non-key attributes in the table are exclusively dependent on the key. In other words: No non-key attribute should depend on another non-key attribute. This can usually be achieved by moving the non-key attribute in question to a new table where its dependency is a key.
4. BCNF (Boyce-Codd Normal Form): Each attribute represents a fact about "the key, the whole key, and nothing but the key". This is often fixed by moving the attribute in question to a new table with only the parts of the original table's key that it cares about. This is an intermediary step between 3NF and 4NF but came about after 4NF, which is why it itself is not 4NF.
5. 4NF (Fourth Normal Form): Every multi-value dependency (2+ values) is either trivial (every {x, y, ...} combination is unique in the table for that relationship) or the independent key in the dependency is a candidate key (only exists once in the table). This is best demonstrated with an example: Suppose you have a table with a key {Restaurant Name, Pizza Type, Delivery Area}. In this example pizza type and delivery area both depend on the restaurant, but do not depend on each other, so it can be split into two tables, one with a {Restaurant Name, Delivery Area} key, and one with a {Restaurant Name, Pizza Type} key.
6. 5NF (Fifth Normal Form): Every non-trivial join relationship is implied by the keys in the table. You can verify 5NF by trying to split a table into new tables and then joining the split tables together. If there is no way to split the original table in a way that the new tables can be joined together to look identical to the original table, then that table satisfies 5NF.

There are actually other normal forms, but they are more nuanced and not as frequently followed.