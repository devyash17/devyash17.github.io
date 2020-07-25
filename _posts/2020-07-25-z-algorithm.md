---
layout: post
title:  "Z-Algorithm"
date:   2020-07-25 22:10:51 +0530
categories: [String Algos]
---

In this algorithm, we build a z-array that contains for each index *i* the length of the longest substring starting from *i* which is also a prefix of *S* where *S* is a given string.
For example, the z-array of *ACBACDACBACBACDA* is as follows:

![image](https://user-images.githubusercontent.com/41137582/88462113-8a752180-cec6-11ea-9c96-8bde1b263633.png)

<br> Z-Algo can be used for pattern searching with **O(n)** time complexity.

Implementation:

{% highlight ruby %}

#  Z[i] is the length of the longest substring starting from S[i] which is also a prefix of S

vector<int> z_function(string s) {
        int n = (int) s.length();
        vector<int> z(n);
        for (int i = 1, l = 0, r = 0; i < n; ++i) {
                if (i <= r)
                z[i] = min (r - i + 1, z[i - l]);
                while (i + z[i] < n && s[z[i]] == s[i + z[i]])
                ++z[i];
                if (i + z[i] - 1 > r)
                l = i, r = i + z[i] - 1;
        }
        return z;
}

{% endhighlight %}
