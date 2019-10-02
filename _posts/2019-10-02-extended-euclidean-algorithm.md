---
layout: post
title:  "Extended Euclidean Algorithm"
date:   2019-10-03 01:00:51 +0530
categories: jekyll update
---

Extended Euclidean Algorithm(EEA), as suggested by its name is an extension of Euclidean Algorithm(EA) that alongside with finding GCD(x,y), also finds a way to represent GCD(x,y) in terms of x and y.
{% highlight ruby %}
a.x + b.y = GCD(x,y)
{% endhighlight %}

Function's Input: x,y
Function's Output: GCD(x,y),a,b
{% highlight ruby %}
GCD, a, b = EEA(x,y)
{% endhighlight %}
In EEA, we will use EA as sub-routine while simultaneously calculating a and b.

Euclidean Algorithm to calculate `GCD(x,y)`, recursively calls `GCD(y%x,x)`.
</br>Let `g = GCD(x,y), x' = y%x,  y' = x`.

`g, a', b' = EEA(x',y')`   // *recursive call*

above statement implies:
</br> `a'.x' + b'.y' = g`

Substituting `x' = y - floor(y/x).x and y' = x`, we get
`(b'-floor(y/x).a').x + a'y = g`

Therefore 
{% highlight ruby %}
a = b' - floor(y / x).a'  and b = a'
{% endhighlight %}
Implementation:

{% highlight ruby %}
int gcd(int x, int y, int & a, int & b) {
    if (x == 0) {
        a = 0;
        b = 1;
        return y;
    }
    int a', b';
    int d = gcd(y % x, x, a', b');
    x = b' - (y / x) * a';
    y = a';
    return d;
}
{% endhighlight %}



