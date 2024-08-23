---
title: ABC串讲——332（A~C）
date: 2024-01-19 21:35:04
tags: C艹
categories: 
- 题解
- AT-ABC串讲
---


# A Online Shopping

模拟计算就得了。

<!--more-->

ACCode：

```cpp
#include <bits/stdc++.h>

#define log printf

using namespace std;

const int N = 10010;
int n, s, k, p[N], q[N], sum;

int main() {
    scanf("%d%d%d", &n, &s, &k);
	for (int i = 1; i <= n;i++)
        scanf("%d%d", &p[i], &q[i]), sum += p[i] * q[i];
	if (sum < s) sum += k;
	log("%d\n", sum);
	return 0;
}
```

[AC记录](https://www.luogu.com.cn/record/140465002)

# B Glass and Mug

还是模拟，建俩变量模拟一遍得了。

ACCode：

```cpp
#include <bits/stdc++.h>

#define log printf

using namespace std;

int k, g, m, gls, mug;

int main() {
    scanf("%d%d%d", &k, &g, &m);
    for (int i = 0;i < k;i++) {
        if (gls == g) gls = 0;
        else
			if (mug == 0) mug = m;
            else {
				int mug_can = mug, gls_need = g - gls;
				if (mug_can > gls_need) gls = g, mug -= gls_need;
                else if (mug_can < gls_need) mug = 0, gls += mug_can;
                else gls += gls_need, mug -= mug_can;
			}
    }
	log("%d %d\n", gls, mug);
	return 0;
}
```

[AC记录](https://www.luogu.com.cn/record/140465914)

# C T-shirts

又双叒叕是模拟。

ACCode：

```cpp
#include <bits/stdc++.h>

#define log printf

using namespace std;

int m, n, plain, logo, logo_have;
string s;

int main() {
	cin >> n >> m >> s;
	plain = m;
	for (int i = 0; i < n; i++) {
		if (s[i] == '0') {
			plain = m;
			logo_have = logo;
			continue;
		}
		if (s[i] == '1') {
			if (plain > 0)
				plain--;
			else {
				if (logo_have > 0)
					logo_have--;
				else
					logo++;
			}
		} else {
			if (logo_have > 0)
				logo_have--;
			else
				logo++;
		}
	}
	log("%d\n", logo);
	return 0;
}
```

~~讲了跟没讲一样。~~

[AC记录](https://www.luogu.com.cn/record/140466860)