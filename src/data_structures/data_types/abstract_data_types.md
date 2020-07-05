# Abstract Data Types

These are models defined by their behavior. Their implementations are not prescribed, which is what separates them from data structures.

### List

A.K.A. sequence.<br>
Countable, ordered values with no requirement for uniqueness.

### Multimap

A series of mappings from unique keys to values.<br>

#### Associative Array

A.K.A. map or dictionary.<br>
A subset of multimaps wherein only one value can be associated with a key.

### Set
 
Unique, unordered values.

### Multiset

A.K.A. bag.<br>
Similar to a set, but can allow repeated (equal) values, which can either be treated as identical (counted, but not stored), or equivalent (counted and stored).<br>
You could also think of it as similar to a list, but order doesn't matter.

### Stack

Like a list, defined by the following behavior:
- *Push* an element by adding it to the front of the list.
- *Pop* an element by removing it from the front of the list.
- *Peek* by observing the front-most element.

The last element to enter the stack will be the first one to leave it.

### Queue

Like a list, defined by the following behavior:
- *Enqueue* an element by adding it to the back of the list.
- *Dequeue* an element by removing it from the front of the list.

The first element to enter the queue will be the first one to leave it.

#### Priority Queue

A subcategory of queue where either the *enqueue* operation or the *dequeue* operation may re-order elements such that certain elements will leave the queue with a higher priority than other elements (first-in-first-out is not as strictly followed).