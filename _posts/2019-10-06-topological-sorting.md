---
layout: post
title:  "Topological Sorting"
date:   2019-10-06 00:00:51 +0530
categories: jekyll update
---

Topological sorting is an ordering of the vertices of a directed graph such that if there is an edge `a->b` between vertices **a** and **b**, then `a` appears before `b` in the ordering. Consider the graph below:
![image](https://user-images.githubusercontent.com/41137582/66259366-d2a74400-e7cd-11e9-9ed0-65cf70b03a97.png)

One possible ordering is `[4,1,5,2,3,6]`
![image](https://user-images.githubusercontent.com/41137582/66259518-8ceb7b00-e7cf-11e9-9ade-17e7d9a53cbb.png)

For a directed graph to have a topological ordering, **it should not contain any cycle**.

We can make use of DFS traversal to both check if the directed graph contains a cycle and, if doesn't, to construct a topological sort.

#### Pseudo code for topological sort:

{% highlight ruby %}

DFS(graph,u)
{
# state[u] = 1 => u has not been processed yet.
# state[u] = 2 => u is under processing.
# state[u] = 3 => u has been processed earlier.
	if(state[u]==3):
		return ;
	else if(state[u] = 2):
		cycle = 1;
		return ;
	else state[u] = 2;
	for every neighbour v of u:
		DFS(graph,v,state)
	
	state[u] = 3; # mark it processed.
	Stack.push(u);
}

topologicalSort(graph)
{
	ordering = []
	state[V] = {1};
	cycle = 0;
	stack Stack;
	for every node u in graph:
		DFS(graph,u)
		
	if cycle == 1:
		return ordering
	
	while Stack is not Empty:
		ordering.add(Stack.top())
		Stack.pop()
	
	return ordering
}

{% endhighlight %}

References: [GeeksforGeeks][gfg]

[gfg]: https://www.geeksforgeeks.org/topological-sorting/

