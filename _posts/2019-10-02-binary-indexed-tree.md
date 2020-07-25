---
layout: post
title:  "Binary Indexed Trees/Fenwick Trees"
date:   2020-07-25 20:19:51 +0530
categories: [Data Structures]
---

A Binary Indexed Tree(BIT) is nothing but a dynamic variant of a prefix sum array. The only difference is that it supports both the range sum queries and the value updates in **O(logn)** time.
The idea behind BIT is that every number can be represented as a sum of powers of 2 and hence we need to update/query on maximum of *logn* different segments. 

To visualize how BIT gets filled, let's take an example. 
Consider the array: 
![image](https://user-images.githubusercontent.com/41137582/88459971-9c4ec880-ceb6-11ea-8f03-e48c8e78c868.png)

The corresponding BIT is:
![image](https://user-images.githubusercontent.com/41137582/88459990-bbe5f100-ceb6-11ea-994b-ad019bbbed81.png)

To get the sum of elements in the range #[i,j]#, we can use **sum(j)-sum(i-1)**.
Similarly, to increase a value at index *i* by *val*, we can simply call **update(i,val)**.

Implementation:

{% highlight ruby %}

#assume 1-based indexing

const int N = 10;
int prefix_sum[N];

int sum(int i)
{
        int ans = 0;
        while(i)
        {
                ans += prefix_sum[i];
                i -= (i & -i);
        }
        return sum;
}

void update(int i,int val)
{
        while(i <= N)
        {
                prefix_sum[i] += val;
                i += (i & -i);
        }
}

{% endhighlight %}