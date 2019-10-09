---
layout: post
title:  "Dijkstra's Algorithm Part 1"
date:   2019-10-08 23:33:51 +0530
categories: [Graph Algos]
---

Dijkstra's Algorithm finds shortest paths from a `src` node to all the vertices of the graph like [Bellman-Ford Algorithm][bf]. However it does not work for the graphs having negative weight edges. The benefit of Dijsktra’s algorithm
is that it is more efficient and can be used for processing large graphs.

**Note**: The below implementation is optimal for [dense graphs][dg].

Time Complexity: **`O`(`n`<sup>`2`</sup> `+ m)`**
where `n`: number of vertices and `m`: number of edges

In case of [sparse graphs][sg], the complexity can be reduced to **`O(n + mlogm)`** using priority queue data structure of STL.

#### Pseudo code for Dijsktra’s Algorithm (for Dense graphs):

{% highlight ruby %}

Dijkstra(Graph,src) # Graph is represented here using adjacency matrix. 
{
	bool processed[V] = {false};
	int distance[V] = {INF};
	distance[src] = 0;
	for i = 1 to i = n-1:
	
	# Get the vertex which is not already processed and 
	# has the least distance value. This step takes O(n) time.
		u = minDist(distance,processed); 
		
		if(distance[u] = INF)  # Now remaining vertices are unreachable from src,
		 break;				   # so break the loop.
		 
		processed[u] = true; # include u in the processed set
		for every neighbour v of u:
		 if(!processed[v]):
		  distance[v] = min(distance[v],distance[u] + Graph[u][v]);		  
}
			

{% endhighlight %}

References: [GeeksforGeeks][gfg]

[bf]: https://devyash17.github.io/graph%20algos/2019/10/06/bellman-ford-algorithm.html
[dg]: https://en.wikipedia.org/wiki/Dense_graph
[sg]: https://xlinux.nist.gov/dads/HTML/sparsegraph.html
[gfg]: https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/
