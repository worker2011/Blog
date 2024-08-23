---
title: ABC串讲——328（A~C）
date: 2024-01-19 21:18:04
tags: C艹
categories:
- 题解
- AT-ABC串讲
---

# A Not Too Hard
$N \le 8$ 也是醉了，循环枚举就得了呗？
遍历一遍数组就可以 AC 了。

<!--more-->

ACCode：

```cpp
#include <bits/stdc++.h>

using namespace std;

const int N = 10;
int n, x, a[N], sum;

int main() {
	scanf("%d%d", &n, &x);
	for (int i = 1;i <= n;i++) {
		scanf("%d", &a[i]);
		if (a[i] <= x)
			sum += a[i];
	}
	printf("%d\n", sum);
	return 0;
}

```

[AC记录](https：//www.luogu.com.cn/record/135867122)

# B 11/11
~~我生日哎。~~

数位最多两位，这个数位分解很简单。这里有一种简单粗暴的办法：如果十位是0就让它等于个位就好了，反正不影响结果。

ACCode：

```cpp
#include <bits/stdc++.h>

using namespace std;

const int N = 110;
int n, d[N], ans;

int main() {
	scanf("%d", &n);
	for (int i = 1;i <= n;i++) {
		scanf("%d", &d[i]);
		for (int j = 1;j <= d[i];j++) {
			int ge = j % 10, shi = j / 10, gei = i % 10, shii = i /10;
			if (shi == 0)
				shi = ge;
			if (shii == 0)
				shii = gei;
			if (ge == shi && shi == gei && gei == shii)
				ans++;
		}
	}
	printf("%d\n", ans);
	return 0;
}
```

[AC记录](https：//www.luogu.com.cn/record/135867314)

# C Consecutive
{% note success%}
Tips：区间求答案，就想前缀和。
{% endnote %}

如果相等，就在答案数组上+1，否则就不加

ACCode with 注释：

```cpp
#include <bits/stdc++.h>

using namespace std;

const int N = 3e5 + 10;
int n, q, l, r, cnt[N];
string s;

int main() {
    scanf("%d%d", &n, &q);
    cin >> s;
    s = ' ' + s;  // 前缀和从1开始
    for (int i = 1;i <= n;i++)
        if (s[i] == s[i + 1])  // 相等
            cnt[i] = cnt[i - 1] + 1;  // 记录
        else
            cnt[i] = cnt[i - 1];
    for (int i = 1;i <= q;i++) {
        scanf("%d%d", &l, &r);
        printf("%d\n",  cnt[r - 1] - cnt[l - 1]);
        /*因为上面是s[i + 1]与s[i]相同就记录了，
        所以要用cnt[r - 1]以防在最后一组相同的区间内只有其中一个字符，
        即避免如aabb中的bb在筛查1~3的时候被计算*/
    }
    return 0;
}
```

~~什么蹩脚英语。~~

[AC记录](https：//www.luogu.com.cn/record/135867500)