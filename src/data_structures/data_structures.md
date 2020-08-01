# Data Structures

These are fundamental structures in computer science which enable complex operations. This chapter only covers data structures that are significant/well-known in computer science, or that are broadly applicable to most computer science fields. You will not find data structures in this chapter that have very specific, niche use cases, or are only applicable to specific fields of computer science.

## Cheat Sheet
For the lazy among you...

### Abstract Data Types
- [List](https://en.wikipedia.org/wiki/List_(abstract_data_type)): ordered, not necessarily unique, not finite
- [Set](https://en.wikipedia.org/wiki/Set_(abstract_data_type)): not necessarily ordered, unique, not finite
- [Tuple](https://en.wikipedia.org/wiki/Record_(computer_science)): ordered, not necessarily unique, finite, a composite type in some (probably most) languages
- [Stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)): first-in-last-out, `pop()`, `push()`, `peek()`
- [Queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type)): first-in-first-out, `enqueue()`, `dequeue()`, can be prioritized (priority queue)
- [Bag](https://en.wikipedia.org/wiki/Set_(abstract_data_type)#Multiset): random or full reads only, `grab()`/`pick()`
- [Multimap/Associative Array](https://en.wikipedia.org/wiki/Multimap): key-value mappings (e.g. hash table), `getValue(key)`, `insert(key, value)`

### Performance Tables

If multiple values, the order is _Worst-Case_ | _Amortized_ .

#### Arrays & Lists
<table>
    <tr>
        <th>Structure</th>
        <th>Indexing</th>
        <th>Insert/Delete [0]</th>
        <th>Insert/Delete [n-1]</th>
        <th>Insert/Delete [i]</th>
        <th>Wasted Space</th>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Array_data_structure">Array</a></td>
        <td>&Theta;(1)</td>
        <td>N/A</td>
        <td>N/A</td>
        <td>N/A</td>
        <td>0</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Dynamic_array">Dynamic Array</a></td>
        <td>&Theta;(1)</td>
        <td>&Theta;(n)</td>
        <td>&Theta;(n) | &Theta;(1)</td>
        <td>&Theta;(n)</td>
        <td>&Theta;(n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Hashed_array_tree">Hashed Array Tree</a>*</td>
        <td>&Theta;(1)</td>
        <td>&Theta;(n)</td>
        <td>&Theta;(n) | &Theta;(1)</td>
        <td>&Theta;(n)</td>
        <td>&Theta;(&#8730;n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Linked_list">Linked List</a></td>
        <td>&Theta;(n)</td>
        <td>&Theta;(1)</td>
        <td>&Theta;(1), &Theta;(n)**</td>
        <td>***</td>
        <td>&Theta;(n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree">Balanced Tree</a>****</td>
        <td>&Theta;(log n)</td>
        <td>&Theta;(log n)</td>
        <td>&Theta;(log n)</td>
        <td>&Theta;(log n)</td>
        <td>&Theta;(n)</td>
    </tr>
</table>
* Not programmatically a tree, contrary to its name.
<br>
** &Theta;(1) when the last element is known; &Theta;(n) when the last element is unknown.
<br>
*** Insertions/Deletions from the middle of a list are dependent how that element is found (it is &Theta;(n) to simply go to the i<sup>th</sup> element, but searching without knowing the index has a different complexity). There is a &Theta;(1) tax on that algorithm.
<br>
**** Not technically a list structure, but included to compare indexing.
<br>
<br>
<table>
    <tr>
        <th>Structure</th>
        <th>Search</th>
        <th>Insert</th>
        <th>Delete</th>
        <th>Space</th>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Skip_list">Skip List</a></td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
        <td>O(n log n) | O(n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Hash_table">Hash Table</a></td>
        <td>O(n) | O(1)</td>
        <td>O(n) | O(1)</td>
        <td>O(n) | O(1)</td>
        <td>O(n)</td>
    </tr>
</table>

#### Trees
<table>
    <tr>
        <th>Structure</th>
        <th>Search</th>
        <th>Insert</th>
        <th>Delete</th>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Binary_tree">Binary Tree</a></td>
        <td>O(n)</td>
        <td>O(n)</td>
        <td>O(n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Binary_search_tree">Binary Search Tree</a></td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Cartesian_tree">Cartesian Tree</a></td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/K-d_tree">K-D Tree</a></td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
        <td>O(n) | O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/AVL_tree">AVL Tree</a></td>
        <td>O(log n)</td>
        <td>O(log n)</td>
        <td>O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Red%E2%80%93black_tree">Red-Black Tree</a></td>
        <td>O(log n)</td>
        <td>O(log n)</td>
        <td>O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Splay_tree">Splay Tree</a></td>
        <td>&Theta;(n) | O(log n)*</td>
        <td>&Theta;(n) | O(log n)</td>
        <td>&Theta;(n) | O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/B-tree">B-Tree</a></td>
        <td>O(log n)</td>
        <td>O(log n)</td>
        <td>O(log n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Trie">Trie</a>**</td>
        <td>O(m)</td>
        <td>O(m)</td>
        <td>O(m)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Van_Emde_Boas_tree">Van Emde Boas Tree</a>***</td>
        <td>O(log m)</td>
        <td>O(log m)</td>
        <td>O(log m)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Radix_tree">Radix Tree</a>**</td>
        <td>O(m)</td>
        <td>O(m)</td>
        <td>O(m)</td>
    </tr>
</table>
* Recently searched values can be found again in O(1) time with splay trees.
<br>
** Tries are a type of associative array, and radix trees are a type of trie. Here, m represents the length of the key.
<br>
*** Van Emde Boas trees are also a type of associative array. Here, m is the bit length of the keys and the maximum number of elements that can be stored in the tree is 2<sup>m</sup>.

#### Heaps
<table>
    <tr>
        <th>Structure</th>
        <th>Find-Min*</th>
        <th>Delete-Min*</th>
        <th>Insert</th>
        <th>Decrease-Key</th>
        <th>Meld</th>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Binary_heap">Binary Heap</a></td>
        <td>&Theta;(1)</td>
        <td>&Theta;(log n)</td>
        <td>O(log n)</td>
        <td>O(log n)</td>
        <td>&Theta;(n)</td>
    </tr>
    <tr>
        <td><a href="https://en.wikipedia.org/wiki/Fibonacci_heap">Fibonacci Heap</a></td>
        <td>&Theta;(1)</td>
        <td>O(log n)</td>
        <td>&Theta;(1)</td>
        <td>&Theta;(1)</td>
        <td>&Theta;(1)</td>
    </tr>
</table>
* "Min" here is used to refer to the value with the highest priority (it is what will be at the top of the heap).

#### Graphs
There aren't that many types of graphs, and the most common non-standard type is a flow network.

Graphs can be searched in \\( O(\left\lvert V \right\rvert + \left\lvert E \right\rvert) \\) time using \\( O(\left\lvert V \right\rvert) \\) space, where \\( \left\lvert V \right\rvert \\) and \\( \left\lvert E \right\rvert \\) are the number of vertices and the number of edges, respectively.

The performance of finding the shortest path between two vertices depends on the type of graph (directed, acyclic, does/does not contain negative edge weights, etc.) and the algorithm used. See more in the algorithms chapter.