# Linear Data Structures

### Dynamic Array

### Hashed Array Tree

### Linked List

A.K.A. singularly linked list.

A list that consists of a sequence of nodes, which each contain a value and a reference to the next node in the list (or null if it is the last node).

- Searchable in O(n) time.
- Insert, delete, or read at the beginning or end of the list in O(1) time.
- Insert, delete, or read in the middle of the list in O(n) time.

### Doubly Linked List

### Circularly Linked List

### Skip List

### Hash Table

An implementation of an associative array that passes provided keys through a hash function to determine where in an array they go.<br>
Key collisions can be handled either by implementing the array as an array of lists (multiple keys can map to the same place, but their order is tracked so as to know which value in the list belongs to which key) or by moving the value to the next available space.

- Does not allow for null keys or values.
- Thread-safe. Not performant.

### Hash Map

Similar to a hash table.

- Allows nulls for keys and values.
- Not thread-safe. Performant.

### Hash Set

Values are passed through a hash function to determine their placement within an array.<br>
Follows the rules of a set.