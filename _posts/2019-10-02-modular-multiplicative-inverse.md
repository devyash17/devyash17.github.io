---
layout: post
title:  "Modular Multiplicative Inverse"
date:   2019-10-02 22:33:51 +0530
categories: jekyll update
---

A modular multiplicative inverse of an integer x is an integer y such that x.y is congruent to 1 modular some modulus m. Mathematically speaking:

{% highlight ruby %}
( x.y ) % m = 1
{% endhighlight %}

It can be proven that such an integer y exists iff `gcd(x,m) = 1` i.e. x and m are relatively prime.

How to find it:
We will use *Extended Euclidean Algorithm (EEA)* to get the value of y (if it exists). We pass x and m as inputs to EEA to get the *gcd(x,m)* and coefficients *c1* and *c2* such that: 
`x.c1 + m.c2 = gcd(x,m)`

Now iff `gcd(x,m)` comes out be 1 then there exists a solution and above equation can be rewritten as:
{% highlight ruby %}
x.c1 + m.c2 = 1
{% endhighlight %}
By taking modulo m on both sides we get:
{% highlight ruby %}
( x.c1 ) % m = 1
{% endhighlight %}

So c1 returned by EEA is our answer.

Implementation:

{% highlight ruby %}
int x, y, g, c1, c2;
g,c1,c2 = EEA(a, m);
if (g != 1) {
    cout << "No solution!";
}
else {
    c1 = (c1 % m + m) % m;
    cout << c1 << endl;
}
{% endhighlight %}

Notice the we way we modify c1. The resulting c1 from the extended Euclidean algorithm may be negative, so `c1 % m` might also be negative, and we first have to add *m* to make it positive.
