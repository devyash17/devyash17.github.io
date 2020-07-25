---
layout: post
title:  "KMP-Algorithm"
date:   2019-11-14 15:43:51 +0530
categories: [String Algos]
---

[KMP-Algorithm][KMP] finds all the occurences of a pattern in a given string. Naive pattern searching algorithm takes **`O(|P|*(|S|-|P|+1))`** time whereas KMP Algorithm's worst case time complexity is **`O(|S|)`** where S is the text string and P is the pattern we are looking for.

For example `S = ABCDABCDAB` and `P = ABCDAB`, then the algorithm should detect the pattern at indices 0 and 4.



#### Pseudo code for KMP-Algorithm:

{% highlight ruby %}

#π[i] is the length of the longest proper prefix of the substring s[0…i] which is also a suffix of this substring

vector<int> computePi(string P) {
 
    int n = P.size();
    vector<int> pi(n,0);
    for (int i = 1; i < n; i++) {
        int j = pi[i-1];
        while (j > 0 && P[i] != P[j])
            j = pi[j-1];
        if (P[i] == P[j])
            j++;
        pi[i] = j;
    }
    return pi;
}

KMP(string S,string P)
{
  #compute prefix array
  vector<int> pi = computePi(P);
  int n = S.size(),m = P.size();
  int i = 0,j = 0;
  while(i < n)
  {
	if(P[j] == S[i])
	i++,j++;

	if(j == m)
	{
	  print(pattern found at: i-j);
	  j = pi[j-1];
	}
	else if(i < N && P[j] != S[i])
	{
	  if(j) j = pi[j-1];
	  else i++;
	}
  }
}

{% endhighlight %}

[KMP]: https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm
 
