# Breadth-First Search => $O(V+E)$
Is a algorithm that discovers shortest path from node *s* to all other nodes in graph $G = (V,\ E)$.
```
BFS(G, s)
for each vertex u in G.V - {s}
	u.color = WHITE
	u.distance = infinit
	u.parent = NIL

s.color = GRAY
s.distance = 0
s.parent = NIL
Q = []
ENQUEUE(Q, s)
While Q != []:
	u = DEQUEUE(Q)
	for each vertex v in G.Adj[u]:         // search the neighbors of u
		if v.color == WHITE:               // is v being discovered now?
			v.color = GRAY 
			v.distance = u.distance + 1
			v.parent = u
			ENQUEUE(Q, v)                  // v is now on the frontier
	u.color = BLACK                        // u is now behind the frontier
```
![[bfs.png]]