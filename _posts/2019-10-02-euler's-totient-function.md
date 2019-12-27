---
layout: post
title:  "Euler's Totient function"
date:   2019-12-28 00:00:00 +0530
categories: [Miscellaneous]
---

Euler’s Totient function `phi(n)` for an input n is count of numbers in {1, 2, 3, …, n} that are relatively prime to n.

#### Pseudo code for Euler's Totient function

{% highlight ruby %}

int phi(int n)
{
	int ans = n;
	for(int p = 2;p*p <= n;p++)
	{
	  if(n%p == 0)
	  {
		while(n%p == 0)
		  n /= p;
		ans -= ans/p;
	  }
	}
	if(n > 1) ans -= ans/n;
	return ans;
}

{% endhighlight %}