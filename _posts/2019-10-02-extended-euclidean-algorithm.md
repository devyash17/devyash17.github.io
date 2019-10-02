---
layout: post
title:  "Extended Euclidean Algorithm"
date:   2019-10-03 01:00:51 +0530
categories: jekyll update
---

Extended Euclidean Algorithm(EEA) as suggested by its name, is an extension of Euclidean Algorithm(EA) that alongside with finding GCD(x,y), also finds a way to represent GCD(x,y) in terms of x and y.
{% highlight ruby %}
a.x + b.y = GCD(x,y)
{% endhighlight %}

Function's Input: `x,y`
Function's Output: `GCD(x,y),a,b`
{% highlight ruby %}
GCD, a, b = EEA(x,y)
{% endhighlight %}
In EEA, we will use EA as sub-routine while simultaneously calculating a and b.

Euclidean Algorithm to calculate `GCD(x,y)`, recursively calls `GCD(y%x,x)`.

Let `g = GCD(x,y), x' = y%x,  y' = x`.

`g, A, B = EEA(x',y')`   <----- *recursive call*

The above statement implies:
`A.x' + B.y' = g`

Substituting `x' = y - floor(y/x).x and y' = x`, we get
{% highlight ruby %}
(B-floor(y/x).A).x + A.y = g
{% endhighlight %}

Therefore 
{% highlight ruby %}
a = B - floor(y / x).A  and b = A
{% endhighlight %}
Implementation:

{% highlight ruby %}
int gcd(int x, int y, int & a, int & b) {
    if (x == 0) {
        a = 0;
        b = 1;
        return y;
    }
    int A, B;
    int d = gcd(y % x, x, A, B);
    a = B - (y / x) * A;
    b = A;
    return d;
}
{% endhighlight %}



