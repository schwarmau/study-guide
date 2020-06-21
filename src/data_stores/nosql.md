# NoSQL
NoSQL databases are exactly what their title claims they are: non-SQL databases. The hallmarks of a NoSQL database are as follows:
- Data storage is flexible by virtue of not being tied to relationships.
- Adherance to the BASE model.
- Efficient implementations of partitioning, clustering, etc. for distribution of data.

Unlike relational systems, which are commonly designed around the entities and normalization of data (relationships are handled later via joins), NoSQL databases are commonly designed with runtime queries in mind. Stores might be created specifically for one query, and there may be redundancies across stores for that reason. Often, redundancies can be avoided, but sometimes they can't be in the name of performance.

There are many NoSQL data stores to choose from, but the most common ones fall under one of these categories:
- Key-Value: These act like dictionaries; They tie a key to a value. These are good for straight-forward lookups.
- Document: Document stores are a dubclass of Key-Value stores wherein all the data is contained in a document, which could have any structure desired (similar to objects in programming). Documents in a database usually do not need to have matching schema. The data in key-value stores are inherently opaque to the database, whereas a document store relies on the internal structure of the document to extract metadata that the database engine can use to optimize transactions. This difference is usually moot.
- Columnar: Columnar data stores store data in columns instead of rows. Traditional, row-based storage will serialize complete records together (e.g. for a "Person" with a "Name" and "Age", you might see `John Smith, 30` and `Daisy Hopkins, 29` as the rows), whereas a columnar storage will serialize complete columns together (for the previous example: `Record 1: John Smith, Record 2: Daisy Hopkins` and `Record 1: 30, Record 2: 29`). The traditional, row-based storage lends itself to drawing relationships between tables, but for simple queries, the columnar store will be much more performant.
- Graph: Graphs store data...in a graph! This adds a layer of relationships to objects in the store, making it useful for storing information about networks and groups, as well as lending itself to pathfinding queries.