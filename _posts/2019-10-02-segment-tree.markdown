---
layout: post
title:  "Segment Tree"
date:   2019-10-03 15:53:51 +0530
categories: jekyll update
---

Segment tree is a data structure that supports range queries such as:

1. `sum(i,j)`: calculate the sum of values in the range [i,j].
2. `min(i,j)`: find the minimum value in the range [i,j].
3. `max(i,j)`: find the maximum value in the range [i,j].
4. `update(i,val)`: modify the ith element of the array. 

One way to handle first three queries is to simply run a loop and do the required operations and get the work done in **O(nq)** time where q is number of queries and n is the size of the array. However if both n and q are large, this approach is slow but with the help of segment trees, we can perform all the above listed operations in **O(qlogn)** time complexity.

References: [Codeforces][cf], [GeeksforGeeks][gfg]

[cf]: https://codeforces.com/blog/entry/18051
[gfg]: https://www.geeksforgeeks.org/segment-tree-efficient-implementation/
