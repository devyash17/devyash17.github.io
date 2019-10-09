---
layout: post
title:  "Dijkstra's Algorithm Part 2"
date:   2019-10-08 23:33:51 +0530
categories: [Graph Algos]
---

Dijkstra's Algorithm finds shortest paths from a `src` node to all the vertices of the graph. However it does not work for the graphs having negative weight edges. The benefit of Dijsktra’s algorithm
is that it is more efficient and can be used for processing large graphs.

**Note**: The below implementation is optimal for [sparse graphs][sg].

Time Complexity: **`O(n + mlogm)`**
where `n`: number of vertices and `m`: number of edges

In [part-1][p1], the time required to find the vertex with the least distance value and not already in the processed set, is of the order of **O(n)** contributing to **O(n<sup>2</sup>)** part of the complexity. 

In this implementation, I am going to show how **priority queue** data structure can be used instead of an array to yield the same functionality but with a better time complexity.

#### Pseudo code for Dijsktra’s Algorithm (for Sparse graphs):

{% highlight ruby %}

vector<vector<pair<int, int>>> adj;

Dijkstra(src) # Graph is represented here using adjacency matrix. 
{
	bool processed[V] = {false};
	priority_queue<pair<int,int>> pq;
	pq.push({0,src});

	while pq is not Empty:
	# Get the vertex which has the least distance value. 
	# This step takes O(1) time because of priority queue.
		u = pq.top().second ;
		pq.pop();
		if(processed[u])
		 continue;
		 
		processed[u] = true; # include u in the processed set
		
		for every edge in adj[u]: # edge = {v,w} => u to v edge has weight w.
		  v = edge.v, w = edge.w; 
		  if(distance[v] > distance[u] + w)
		   distance[v] = distance[u] + w);
		   pq.push({-distance[v],v});
}			

{% endhighlight %}

**Note**: Negative value of distance is pushed to the priority queue because we want the minimum distance vertex to be at the top but the default version of C++ priority queue keeps maximum element at the top.

References: [cp-algorithms][cpa]

[p1]: https://devyash17.github.io/graph%20algos/2019/10/08/dijkstra's-algorithm-(part-1).html
[sg]: https://xlinux.nist.gov/dads/HTML/sparsegraph.html
[cpa]: https://cp-algorithms.com/graph/dijkstra_sparse.html
