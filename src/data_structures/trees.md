# Trees

Trees are basically rooted graphs (interactions with trees begins at the same vertex each time, which is the root).

Some terminology:
- An element is referred to as a *node*.
- The starting node, with no parent, is called the *root*.
- *External nodes*, or *leaves* are the nodes with no children. *Internal nodes* are the opposite.
- The *height* of a tree is the length of the longest path to a leaf from the root.
- A tree is *balanced* if the left and right subtrees of every node differ in height by no more than 1.

All trees listed below use \\( O(n) \\) space.

Trees can have very complex implementations, so the implementations will not all be described here. The important part is knowing which trees are important for which tasks; You can always google the implementation once you know what you need.

### Binary Tree

In a binary tree, no node can have more than two child nodes. This leads to some handy properties:
- The maximum number of nodes at level \\( l \\) will be \\( 2^{l-1} \\). Note: The root node is considered to be on level 1.
- The maximum number of nodes in a binary tree of height \\( h \\) is \\( 2^h - 1 \\). Note: The height of a tree with one node (the root node) is considered to be 1.
- In a binary tree with \\( n \\) nodes, the minimum height is \\( \log_2(n+1) \\).

Many correlaries can be drawn from the aforementioned properties as well.

There are various ways of describing binary trees based on their structure:
- A __full__ binary tree is one in which every node has either 0 or 2 children. Recursively: A full binary tree is either a single node, or a node with 2 children that are each full binary trees.
- A __complete__ binary tree is one in which every level except the last must be completely filled, and all nodes on the last level must be as far left as possible.
- A __perfect__ binary tree is one in which all leaves are on the same level.

### Binary Search Tree

The basic process of inserting into a binary search tree is as follows:
```
insert(value)
{
    if root.value == null
        root.value = value
    else if value <= root.value
        root.left.insert(value)
    else
        root.right.insert(value)
}
```

The expected height of a binary search tree is \\( \sqrt n \\).

Searching, inserting, and deleting all take, on average, \\( O(\log n) \\) time and, at worst, \\( O(n) \\) time.

### AVL Tree

In an AVL tree, the nodes are ordered, from left to right, minimum to maximum, and the tree stays as balanced as possible.

The basic process of inserting is similar to that of a binary search tree, except that after an insertion, the ancestors of the new node are checked for balance and, if they are not balanced, they get re-balanced.

AVL trees are similar to red-black trees in terms of operational performance, but AVL trees are faster for lookup-intensive applications because they are more strictly balanced.

Searching, inserting, and deleting all take \\( O(\log n) \\) time.

### Splay Tree

Splay trees can really use whatever ordering they want, but the important part is that there is an order, because splay trees have the unique behavior of "splaying" once a node is accessed. Splaying enacts a series of rotations/swaps with the accessed node and its parent or siblings, repeatedly, until the accessed node becomes the root node and the tree still adheres to its ordering principle. This means that splay trees are very performant when it is known that some nodes will be need to be accessed much more frequently than others.

Searching, inserting, and deleting all take, on average, \\( O(\log n) \\) time and, at worst, \\( O(n) \\) time.

### Trie

What makes a tree a trie is if all nodes have a key that is some character to accompany its value. Thus, a traversal through a trie results in a path that creates a unique word/string out of the keys. This also makes it an associative array implementation.

Searching, inserting, and deleting all take \\( O(m) \\) time, where \\( m \\) is the length of the word/string being accessed or updated.

### Cartesian Tree

Cartesian trees are heap-ordered (largest values on top, smallest at bottom, or vice-versa) trees generated from a sequence of numbers (each node represents one of the numbers in the sequence) with the unique property that a symmetric (in-order/left-to-right) traversal of the tree will yield the sequence it was generated from. It takes linear time to construct such a tree.

These trees are commonly used for range-searching operations and range minimum queries.

Searching, inserting, and deleting all take, on average, \\( O(\log n) \\) time and, at worst, \\( O(n) \\) time.

### K-D Tree

Every leaf node in a k-d tree represents a k-dimensional point. Each level down the tree splits that point on another dimension. 

For example, in a 2-d tree, the root node may represent a 1-dimensional line with the formula \\( y = x \\). In this tree, every leaf node to the left of the root will represent a point \\( (x,y) \\) where \\( y \lt x \\), and every leaf node to the right of it will represent a point where \\( y \gt x \\). You could keep creating divisions at each level until eventually you make leaf nodes with the actual coordinates of the points.

This type of tree lends itself to range-searching operations and nearest neighbor problems.

Searching, inserting, and deleting all take, on average, \\( O(\log n) \\) time and, at worst, \\( O(n) \\) time.

### Red-Black Tree

In a red-black tree, each node is assigned a color (red or black), and the tree is given a pattern. If that pattern gets broken by an insertion or deletion, then the tree is re-arranged to reform the pattern of colors. Usually the rule is that colors must alternate.

Searching, inserting, and deleting all take \\( O(\log n) \\) time.

### B-Tree

A B-tree is a non-binary tree that stores nodes in groups and remains balanced. Instead of a node having children, groups of nodes have shared children. This is used for databases and file systems since it is well-suited for storage systems that read and write relatively large blocks of data.

Searching, inserting, and deleting all take \\( O(\log n) \\) time.

### Van Emde Boas Tree

A unique tree that implements an associative array, whose search time improves as the stored values decrease in bit size.

Searching, inserting, and deleting all take \\( O(\log m) \\) time, \\( m \\) is the bit length of the keys, and the maximum number of elements that can be stored in the tree is \\( 2^m \\).

### Radix Tree

A radix tree is a type of trie which is space-optimized. Each node that is an only child is merged with its parent, so instead of a path like g-l-a-d-i-a-t-o-r, you may get a path like g-l-adi-a-to-r.

These share the performance of tries, with some optimizations on searching and some taxes on inserting/deleting.

Searching, inserting, and deleting all take \\( O(m) \\) time, where \\( m \\) is the length of the word/string being accessed or updated.

### Heap

Heaps are types of trees that are commonly used to implement priority queues. Heaps are almost _complete_ trees, and usually they either sort by low-to-high or high-to-low from top-to-bottom.

Some common operations include:
- Find-Min (find the highest priority node)
- Delete-Min (delete the highest priority node)
- Insert
- Increase-Key/Decrease-Key (update the priority of a key/node in the tree)
- Meld/Merge (join 2 heaps together)
- Heapify (turn a list of elements into a heap)

### Binary Heap

These are simply heaps wherein nodes can only have 2 children.

Finding takes \\( \Theta(1) \\) time, deleting \\( \Theta(\log n) \\), inserting and modifying the key \\( O(\log n) \\), and melding/merging \\( \Theta(n) \\).

### Fibonacci Heap

A fibonacci heap is actually a collection of heap-ordered trees, which maintains its status as a heap by keeping track of the minimum value between all the trees. The sizes of the trees are limited by the fibonacci numbers, hence the name. A fibonacci heap is guaranteed to be more performant than a binary heap in cases where insertions and modifications are more likely to happen than deletions.

Finding, inserting, modifying, and merging should all take \\( \Theta(1) \\) time, with deletions taking \\( O(\log n) \\).