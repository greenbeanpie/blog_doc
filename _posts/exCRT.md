---
title: 扩展中国剩余定理(exCRT)模板
date: 2023-10-31 14:27:28
categories:
- 编程
tags:
- C++
- 模板
- 数论
---

解释等到赛前复习模板的时候再写。

```cpp
int excrt(pair<ll, ll>* num,int n)
{
	int m1 = num[0].second, a1 = num[0].first;
	int x, y;
	for (int i = 1; i < n; i++)
	{
		int m2 = num[i].second, a2 = num[i].first;
		// m_1 * x - m_2 * y = a2 - a1;
		int abgcd;
		pair<int,int> xy = exgcd(m1, m2, abgcd);
		int c = (a2 - a1 % m2 + m2) % m2, mod = m2 / abgcd;
		x = xy.first, y = xy.second;
		x = x * c / abgcd % mod;
		a1 += m1 * x ;
		m1 = lcm((ull)m2, (ull)m1);
		a1 = (a1 % m1 + m1) % m1;
	}
	return (a1 % m1 + m1) % m1;
}
```