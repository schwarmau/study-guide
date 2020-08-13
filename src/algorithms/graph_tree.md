# Graph & Tree

### Find the lower common ancestor in a tree or directed acyclic graph (Tarjan's Off-Line Lowest Common Ancestors Algorithm)

Recall that the lowest common ancestor of two nodes in a tree is the lowest node in the tree with those two nodes somewhere in its subtrees.

The basic premise is to follow a post-order traversal of the tree, keeping track of 
The simplified process of finding the lowest common ancestor of nodes _u_ and _v_ in a tree rooted at _root_ is as follows:
```
function getLcs(root, u, v)
    root.ancestor -> root
    for each child in root.children // left-to-right order
        getLcs(child, u, v)
        child.ancestor -> u.ancestor
    if root is u and v is visited
        return v.ancestor
    else if root is v and u is visited
        return u.ancestor
    root.isVisited = true
```

By pre-processing the tree into arrays, one where arr[i] is the visitation status of node _i_ and one where arr[i] is the ancestor of node[i], you can reduce the time complexity of some operations.

A refined variation of this algorithm can perform in linear (\\( O(n) \\)) time.

### Measure the importance of a website (PageRank)

The PageRank algorithm was the original Google. The underyling assumption is that more important websites are likely to receive links from other websites, thus the PageRank algorithm works by performing a web crawl and counting the number and quality of links to pages to determine how important they are.

More info [here](https://en.wikipedia.org/wiki/PageRank).

### Compute the maximum flow in a flow network or directed graph (Ford-Fulkerson Algorithm, Edmonds-Karp Algorithm)

Recall that finding the maximum flow in a flow network entails finding which path through the flow network will allow you to end the path with the highest amount of flow possible.

For this problem there are two algorithms: Ford-Fulkerson and Edmonds-Karp. The difference being that the Ford-Fulkerson algorithm is more of a prescribed idea, whereas the Edmonds-Karp algorithm is actually a fully implemented and optimized version of the Ford-Fulkerson algorithm.

The inputs to the problem consist of a flow network (a graph), a flow capacity, a source node, and a sink node.

To solve the problem you start by assigning all edges a value of 0. Using a breadth-first search approach to traversing the graph, you can generate a list of possible paths to get to the sink node from the source node. In the process of "searching", you are stopping when you find a path that reaches the sink node. At that point in time you will figure out the minimum capacity among the edges from the source to the sink in that path, and add that minumum value to the edges in that path. Your search then continues, but the key here is that, as you continue determining the minimum capacity of edges in a path, you use the _remaining_ capacity of the edges, _not_ the actual capacity. So if you have already assigned an edge a value of 3 and its capacity is 5, then its new capacity is 2 for all future calculations.

The time complexity of the Edmonds-Karp algorithm is \\( O(VE^2) \\), where _V_ is the number of nodes, and _E_ is the number of edges.

### Find the minimum  cut of a graph (Karger's Algorithm)

Recall that the minimum cut of a graph is a slice through the graph which intersects the least amount of edges in the graph.

Karger's algorithm picks a neighboring pair of vertices at random and contracts the edge connecting them (the two nodes are merged, and their edges are moved to the new node), then repeats the process on the newly created graph until there are only two vertices left. The determined cut is then the one which goes through the edges connecting the final two vertices. The algorithm follows the monte carlo formula at its core, and thus does not _guarantee_ the correct answer, but has a high probably of finding the correct answer, especially if repeated a sufficient number of times.

As a monte carlo algorithm, the probability of success is more important than the runtime, as you will want to run it enough times to increase the probability of success to within whatever your personal threshold is. More info [here](https://en.wikipedia.org/wiki/Karger%27s_algorithm#Analysis)

### Find the minimum spanning tree of an undirected, edge-weighted graph (Kruskal's Algorithm, Prim's Algorithm)

The main difference between Kruskal's algorithm and Prim's algorithm is that Kruskal's will work on a disconnected graph (it can find the minimum spanning forest). Also, against a sufficiently dense graph, Prim's algorithm can be made to run in linear time.

Recall that a minimum spanning tree is a subset of the edges of a weighed, undirected graph that connects all the vertices together without containing any cycles and with the minimum weight possible.

Kruskal's algorithm starts by creating a list of forests consisting of one node from the graph (each node is its own forest). Then, the edges in the graph are sorted by weight. One-by-one, the lightest edge is remove from the graph. If that edge connects two forests, then it is added to the minimum spanning tree, and the two forests are joined into one forest. This process is repeated until all a spanning tree is established. This is essentially a modified greedy algorithm.

Kruskal's algorithm runs in \\( O(E \log E) \\) time.

Prim's algorithm is a more of a pure greedy algorithm. Starting from an arbitrary vertex in the graph, choose the minimum weighted edge connected to that vertex that does not connect to a vertex already covered by the spanning tree in progress.

Prim's algorithm [typically] runs in \\( O(E + V \log V) \\) time (though it depends on the data structure used to implement it).

### Find the shortest path between two points in a weighted graph with only non-negative weights (Dijkstra's Algorithm)

Dijsktra's algorithm is a classic algorithm for finding the shortest path between two points in a weight graph. The applications of the algorithm are plentiful. This algorithm is the fastest knwon for finding the shortest path in an arbitrary directed graph with unbounded and non-negative edge weights. However, for more specialized cases (bounded edge weights, integer-only edge weights, directed acyclic graphs, etc.), there also exist more specialized variants that can do them a little faster.

Dijsktra's algorithm is as follows: All nodes are marked as having a distance from the source node of infinity and are unvisited. The source node is then given a distance value of 0 (it is 0 distance from itself). Starting at the source node, all neighboring nodes are analyzed to determine what their distance from the source would be if the path goes through them: the neighboring nodes are given a tentative distance value equal to the current node's distance value plus the distance it is from the current node; If the tenative value is less than its current value then its current value is replaced with the tentative one. Once all neighbors are analyzed, the current node is set as visited. The process is then repeated with the node that currently has the lowest distance value that has not been visited. Once the target node is reached, the algorithm ends, and you simply walk backwards, choosing the nodes with the shortest assigned distance, until you are back at the source in order to determine the shortest path.

Dijkstra's algorithm runs in \\( O(E + V \log V) \\) time when implemented with a fibonacci heap, but the amortized runtime can be improved to \\( O(E + V \log \frac E V \log V) \\) using binary heaps.

### Find the shortest path between two points in a weighted graph (Bellman-Ford Algorithm)

The Bellman-Ford algorithm solves the same problem as Dijkstra's algorithm, except that it can accommodate negative edge weights. The caveat is that if there is a cycle in the graph that totals to a negative value from edge weights, then obviously the solution would involve indefinitely following that loop.

While Dijkstra's algorithm greedily selects the closest vertex that has not been visited after assigning distances, the Bellman-Ford algorithm simply repeats the process for _every_ vertex, thus doing away with the need to denote vertices as "visited". At the end of the process, the same walk backwards from the target is performed. The algorithm thus takes \\( O(E \cdot V) \\) time.

### Solve the traveling salesman problem (Nearest Neighbor Algorithm, Brute Force Algorithm)

The goal of the traveling salesman problem is to determine the fastest route a salesman can take that goes through all the different cities they want to visit and then returns to the starting city.

There are two approaches to this problem: The brute force approach and the nearest neighbor approach.

The nearest neighbor algorithm uses the greedy method to select the nearest city to the one you are currently at that has not already been visited. This is only an approximate solution.

The brute force algorithm simply calculates the distance of every possible path (stopping if the path goes longer than the current minimum).

This problem is used as a benchmark for many optimization methods, as it is computationally difficult and applicable to many real-world problems.

### Solve the knight's tour problem (Warnsdorff's Rule)

The knight's tour problem has the goal of determining what sequence of moves a knight can make on a chess board that brings it to every square exactly once, ending on the square it started on. It is an instance of the more general Hamiltonian path problem in graph theory (try to hit every vertex in a graph exactly once).

Warnsdorff's rule is heuristic that dictates one should choose to move the knight to the square from which it will have the fewest possible moves (in essence being a greedy method solution). In practice, not all Hamiltonian path problems can be solved in this way, but there are many special cases where the heuristic does apply, and thus it's not a bad idea to try applying this heuristic if you encounter such a problem.

### Traverse a graph in search of a specific vertex or value (Breadth-First Search, Depth-First Search, Best-First Search)

#### Breadth-First Search

Check the starting node, then check each adjacent node to the start, then check each adjacent node to the adjacent nodes, and so on. In a tree, this amounts to searching an entire level before moving on to the next.

\\( O(V + E) \\) time and O(V) space.

#### Depth-First Search

Check the starting node, then, for each adjacent node, repeat this process. In a tree this amounts to searching a lineage/branch before moving on to the next.

\\( O(V + E) \\) time and O(V) space.

#### Best-First Search

Choose which node to explore next by some pre-determined rule. The runtime is thus not constant.

### Traverse a tree in search of a specific node or value (Breadth-First Search, Depth-First Search, Best-First Search, Pre-Order Traversal, In-Order Traversal, Post-Order Traversal)

Trees have the same standard traversal methods as graphs (because trees are, in effect, a specialized graph), but the starting node is always the root. Additionally, there are some common orderings when performing a depth-first search:

#### Pre-Order Traversal

```
function POT(root)
    nodes.add(root)
    POT(root.left)
    POT (root.right)
```

#### In-Order Traversal

```
function IOT(root)
    IOT(root.left)
    nodes.add(root)
    IOT(root.right)
```

### Post-Order Traversal

```
function POT(root)
    POT(root.left)
    POT(root.right)
    nodes.add(root)
```

### Find the largest clique in a graph (MaxClique/MaxCliqueDyn Algorithm)

Recall that a clique is a subset of vertices in a graph which are all adjacent to each other (also called a complete subgraph). To find a max clique is to find a clique in a graph which contains the most nodes of any clique in the graph.

The MaxCliqueDyn algorithm is variation of MaxClique which can handle dynamically varying bounds on the clique size. More info [here](https://en.wikipedia.org/wiki/MaxCliqueDyn_maximum_clique_algorithm)