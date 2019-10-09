---
layout: post
title:  "Strongly Connected Components"
date:   2019-10-04 17:33:51 +0530
categories: jekyll update
---

A directed graph is strongly connected if there is a path from every vertex to all the other vertices in the graph.

The strongly connected components(SCCs) of a graph divide the graph into strongly connected parts as large as possible. For example consider the following graph:

![image](https://user-images.githubusercontent.com/41137582/66206262-3564e680-e6cd-11e9-9cc6-308e66003cee.png)

Its strongly connected components are:

![image](https://user-images.githubusercontent.com/41137582/66206331-6ba26600-e6cd-11e9-965a-450831681dd9.png)

The corresponding component graph is:

![image](https://user-images.githubusercontent.com/41137582/66206985-39920380-e6cf-11e9-99cc-fa762250e5ae.png)

The components are `A = {1,2}, B = {3,6,7}, C = {4} and D = {5}.

A component graph is always a directed acyclic graph or DAG.

The number of SCCs in a graph can be computed using Kosaraju's Algorithm which uses two DFS traversals (one of the original graph and the other of the transposed graph).

Pseudocode to get the number of SCCs in a graph:

{% highlight ruby %}

DFS(graph,u,type)
{
# type = 1 => fill the stack
# type = 2 => simple DFS
	if(visited[u]) return; 
	else visited[u] = true; 
	for every neighbour v of u:
		DFS(graph,v,type);
	
	if(type == 1)
	Stack.push(u); # now push it to the stack after pushing every reachable vertex from it.
}
	
countSCC(graph)
{
	count = 0;
	stack Stack ;
	visited[V] = {false};
	for every node u in graph:
		DFS(graph,u,type=1);
	Graph gT = transpose(graph);
	visited[V] = {false};
	while Stack is not Empty:
		u = Stack.top();
		Stack.pop();
		if(!visited[u]):
			DFS(gT,u,type=2);
			count++;
	return count;
}	

{% endhighlight %}
