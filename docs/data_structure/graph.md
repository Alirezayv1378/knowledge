# Graph
- A graph is just:
	- A set of vertices (nodes)
	- A set of edges (connections) between them.

## Graph Representation
### Adjacency Matrix
- An $N \times N$ matrix where:
	- Rows represent source nodes
	- Columns represent destination nodes
	- `matrix[i][j] = 1` if there's an edge from $i \to j$, `0` if there isn't.
- **Properties:**
	-  Maximum possible edges for `N` nodes = $N^2$
	- Space complexity: $O(N^2)$
	- Checking if edge (i, j) exists: $O(1)$ (instant lookup)
	- Iterating over neighbors: $O(N)$
- **When to use:**
	- N is small (< few thousand typically)
	- graph is dense (many edges)
	- You need extremely fast edge lookups
	- You're doing matrix-based operations (e.g., Floyd–Warshall, transitive closure)
	
### Adjacency List
- An array (or map) of lists:
	- Each index corresponds to a node
	- Each entry stores only it's neighbors
- **Properties:**
	- Space complexity: $O(N + E)$
	- Checking if edge exists: $O(degree\ of\ node)$
	- Iterating over neighbors: $O(degree\ of\ node)$
- **When to use:**
	- Graph is large
	- Graph is sparse
	- You care about traversal (BFS, DFS, Dijkstra)

![[adj_list_matrix.png]]
