---
title: 扩展欧拉定理(exGCD)模板
date: 2023-11-01 11:39:57
categories:
- 编程
tags:
- C++
- 模板
- 数论
---

解释：咕咕咕。

```cpp
int exgcd(int a, int b, int &x, int &y)
{ // ax+by=gcd(a,b)
	if (!b)
	{
		x = 1, y = 0;
		return a;
	}
	auto ans = exgcd(b, a % b, y, x);
	y -= a / b * x;
	return ans;
}
```