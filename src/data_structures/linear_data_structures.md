# Linear Data Structures

### Dynamic Array

This is array that can shrink or expand in size. A somewhat basic implementation of this is creating a new array with length of, for example: 16. When the array becomes full, a new array is created with more spaces (different implementations may create a different amount of spaces), for example: 32. Then, all the values in the old array are copied into the new array. The same operation may happen in reverse if enough values are deleted from the array.

The average cost to insert or delete at a random index is therefore \\( \Theta(1) \\), but to insert or delete at the beginning or end of the array is \\( O(n) \\). Dynamic arrays usually waste \\( \Omega(n) \\) space when expanding.

### Hashed Array Tree

Despite the name, this is not really a tree; It's a dynamic array. The difference is that elements are stored as lists. 

For example, your base array may start with a capacity of 16. Actually, it would be an array of length 4, where each element is a pointer to another array of length 4. 

This approach puts some restrictions on when it can be expanded and shrunk, but it means that you only have to move 4 elements (the pointers) instead of 16 when you do expand it. The insertion and deletion performance of the hashed array tree is therefore the same as in a standard dynamic array, but it only wastes \\( O\left(\sqrt n\right) \\) space when expanding.

### Singularly Linked List

A list that consists of a sequence of nodes, which each contain a value and a reference to the next node in the list (or null if it is the last node).

- Searchable in \\( O(n) \\) time (unsorted). Variable when sorted (depends on algorithm).
- Reading, inserting or deleting at the end of the list may take \\( O(1) \\) or \\( O(n) \\) time, depending on whether the last element is known or not (it is known in most implementations).
- Reading, inserting or deleting at the beginning of the list should take \\( O(1) \\) time.
- Insert, delete, or read in the middle of the list in _search time_ + \\( \Theta(1) \\) (always \\( O(i) \\) time if acting on index \\( i \ne n-1 \\)).

### Doubly Linked List

The main difference between a doubly linked list and a singularly linked list is that nodes also carry a reference to the previous node. This may lend itself to sorting algorithms, and if the last element is known in the implementation, then it will always take at most \\( O\left(\frac n 2 \right) \\) time to read/insert/delete at a specific index (time is still that of a singularly linked list if looking for an element by value instead of index).

### Circularly Linked List

A circularly linked list is simply a linked list where the "next" pointer of the last node points to the first node. There is no substantial performance difference between this and a singularly linked list. A circularly linked list can optionally be implemented with doubly linked nodes, thus gaining the benefits of a doubly linked list.

### Skip List

A skip list is quite a unique list. It is a tiered structure, where each tier is itself a sorted list (commonly a linked list). At the top you have a list with few elements, and as you progress down, the lists gain more and more elements (including the elements from previous tiers). Usually there is some sort of algorithm to determine which elements go in the top tier (usually the most frequently accessed elements end up there). This kind of data structure is known as a probabilistic data structure.

A search through a skip list would start at the top and work its way down when it cannot find the desired element. It goes through elements until it passes from a smaller element to a larger element than the one desired, then it will go down to the next tier and search between those two elements in the that tier, and so on. To go to a specific position it can simply jump to the bottom tier or, if it knows the highest tier that the index is on, it can jump straight to the highest tier with that index.

This kind of list is good for storing data with values of varying importance, such as data following a normal curve.

To achieve the performance benefits of a skip list, you must accept wasted space. A skip list will use \\( O(n \log n) \\) space in the worst case, but \\( O(n) \\) on average in exchange for searching, inserting, and deleting in \\( O (\log n) \\) time on average and \\( O(n) \\) time in the worst case.

### Hash Table

An implementation of an associative array that passes provided keys through a hash function to determine where in an array they go.

Key collisions can be handled either by implementing the array as an array of lists (multiple keys can map to the same place, but their order is tracked so as to know which value in the list belongs to which key) or by moving the value to the next available space.

Hash tables...
- do not allow for null keys or values.
- are thread-safe, but not performant.

Hash tables will use the standard \\( O(n) \\) space with constant time (\\( O(1) \\)) searches, insertions, and deletions on average (\\( O(n) \\) in the worst case).

### Hash Map

This is a volatile variation of the hash table, which...
- allows nulls for keys and values.
- is not thread-safe, but is performant.

### Hash Set

A set in which values are passed through a hash function to determine their placement within an array. All other rules of sets are followed (unique, unordered values).