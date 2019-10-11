---
layout: post
title:  "Prim's Algorithm"
date:   2019-10-11 23:33:51 +0530
categories: [Graph Algos]
---

A spanning tree of a graph consists of all vertices and some of the edges of the graph so that there is a path between any two vertices. Therefore, spanning trees are connected and acyclic. Consider the graph below:

![image](https://user-images.githubusercontent.com/41137582/66673823-13480700-ec7f-11e9-988f-9c3f36ff3156.png)

One possible spanning tree for the above graph is:

![image](https://user-images.githubusercontent.com/41137582/66673886-34a8f300-ec7f-11e9-8fd4-133373137b56.png)

The weight of a spanning tree is defined as sum of the weights of all the edges of it. For instance, weight of the above spanning tree is `3 + 5 + 9 + 3 + 2 = 22`.

A **minimum spanning tree (MST)** is a spanning tree whose weight is as low as possible. For example, the weight of the minimum spanning tree of the example graph is 20. One such MST can be drawn like this:

![image](https://user-images.githubusercontent.com/41137582/66674256-1abbe000-ec80-11e9-9cc2-05523c53ddf2.png)

**Note**: MST is not unique and a graph can have several MSTs.

This implementation of [Prim's Algorithm][pa] is pretty much similar to [Dijkstra's Algorithm][da] and works well with [sparse graphs][sg].
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/PrimAlgDemo.gif/200px-PrimAlgDemo.gif)

Time Complexity: **`O(n + mlogm)`**
where `n`: number of vertices and `m`: number of edges

#### Pseudo code for Prim's Algorithm

{% highlight ruby %}

PrimMST(Graph,V) # Graph is represented here using adjacency matrix.
{
	int key[V] = {INT_MAX};
	bool set[V] = {false};
	priority_queue<pair<int,int>> pq;
	key[0] = 0;
	pq.push({0,0});
	while pq is not Empty:
		u = pq.top().second;
		pq.pop();
		if(set[u]) continue;
		set[u] = true;
		
		for i = 1 to i = V:
		 if(graph[u][v]!=INT_MAX && !set[v] && graph[u][v]<key[v]):
		  key[v] = graph[u][v];
		  pq.push({-key[v],v});

}

{% endhighlight %}

References: [GeeksforGeeks][gfg],[cp-algorithms][cpa]

[pa]: https://en.wikipedia.org/wiki/Prim%27s_algorithm
[da]: https://devyash17.github.io/graph%20algos/2019/10/08/dijkstra's-algorithm-(part-2).html
[sg]: https://xlinux.nist.gov/dads/HTML/sparsegraph.html
[gfg]: https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/
[cpa]: https://cp-algorithms.com/graph/mst_prim.html



	
	
	
	