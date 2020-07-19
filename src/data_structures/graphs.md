# Graphs

Graphs are collections of vertices (a.k.a. nodes) and edges, where each vertex has a collection of edges it touches, and each edge is composed of a *to* vertex and a *from* vertex. They are primarily used for spatial operations or relationship analysis.

### Directed Graph

Edges can only be traversed one way. Vertices have their collection of edges split in two: one collection for incoming edges and one collection for outgoing edges.

### Directed, Acyclic Graph

Directed graphs are acyclic if there is no way to traverse from any one vertex back to itself.

### Flow Networks

Edges in a flow network are assigned a flow, and each vertex must have the same incoming flow as it has outgoing flow, except for source vertices, which may not have any incoming flow, and sink vertices, which may not have any outgoing flow. Edges are assigned a capacity, and the flow through edges cannot exceed their capacity.

### Adjacency List
This is a way of representing a graph as a list of node adjacencies.