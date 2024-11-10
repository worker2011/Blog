---
title: 【置顶】珍爱生命，远离 double
date: 2024-08-07 12:59:26
tags:
sticky: 9
thumbnail: /images/double.png
---

rt，今日模拟赛时，某只小 L 看到了 T1，发现是个百分数计算裸题，于是飞速写下了下面的代码：

<!--more-->

```cpp
double tmp;
...
scanf("%d%d", &n, &x);
	FOR(i, 1, n) scanf("%d%d", &v[i], &p[i]);
	FOR(i, 1, n) {
		tmp += v[i] * (p[i] * 0.01), ++ans;
		if (tmp > (x * 1.0)) break;
	}
	if (tmp < (x * 1.0)) log("-1\n");
	else log("%d\n", ans);
```

然后呢？100-->40，rk4-->rk7

小 L 衷心希望大家不要再犯同样的错误……
