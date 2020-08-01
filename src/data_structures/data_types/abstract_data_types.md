# Abstract Data Types

These are models defined by their behavior. Their implementations are not prescribed, which is what separates them from data structures and composite data types.

### List

A.K.A. sequence.

Countable, ordered values with no requirement for uniqueness.

Common operations include `getElementAt(i)`, `add(element)`, `add(element, index)`, `count()`, `first()` and `last()`.

### Multimap

A series of mappings from unique keys to values.<br>

#### Associative Array

A.K.A. map or dictionary.

A subset of multimaps wherein only one value can be associated with a key.

### Set
 
Unique, unordered values.

### Multiset

A.K.A. bag.

Similar to a set, but can allow repeated (equal) values, which can either be treated as identical (counted, but not stored), or equivalent (counted and stored). You could also think of it as similar to a list, but order doesn't matter.

### Stack

Like a list, defined by the following behavior:
- `push(element)` an element by adding it to the front of the list.
- `pop()` an element by removing it from the front of the list.
- `peek()` by observing the front-most element.

The last element to enter the stack will be the first one to leave it.

### Queue

Like a list, defined by the following behavior:
- `enqueue(element)` an element by adding it to the back of the list.
- `dequeue()` an element by removing it from the front of the list.

The first element to enter the queue will be the first one to leave it.

#### Priority Queue

A structure defined with the same behavior as a queue, except either the `enqueue()` operation or the `dequeue()` operation may re-order elements such that certain elements will leave the queue with a higher priority than other elements (first-in-first-out is not as strictly followed).