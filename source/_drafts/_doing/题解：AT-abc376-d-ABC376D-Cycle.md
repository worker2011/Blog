---
title: 题解：AT_abc376_d [ABC376D] Cycle
date: 2024-10-20 18:08:14
tags: C艹
categories: 题解
---

水沝淼㵘的一道 D。

听说 CSP 考前写 tj 可以让 rp += inf？~~于是我连肝两篇。~~

---

题目大意：非常简单，给一个有向无权图，求从点 1 开始能否走到环。如果能，输出所有环中边数最少的那个环的边数，否则输出 `-1`。

最少的，那么肯定是搜索了。具体是 dfs 还是 bfs 呢？其实都可以，因为要求最少，所以 bfs 更加适合。

这里主要介绍两个细节：

一是如何判环。方法是开一个 vis 数组，如果搜了半天发现迂回来了就可以了。“回来”的判断可以用是不是又回到了节点 1 来进行，这样子刚刚好围起来，不多不少。注意一定要及时 `return` 或者 `break`，否则自然就无限在环上饶下去啦~

二是如何输出。如何知道走了多少呢？把 vis 数组改成 int 型的就可以啦，$vis_i$ 记录上次访问 $i$ 是在什么时候，然后把开始时设为 1 就结束了。

---

ACCode（bfs）：

```cpp
/*Code by Leo2011*/
#include <bits/stdc++.h>

#define INF 0x3f3f3f3f
#define EPS 1e-8
#define FOR(i, l, r) for (int(i) = (l); (i) <= (r); ++(i))
#define log printf
#define IOS                      \
	ios::sync_with_stdio(false); \
	cin.tie(nullptr);            \
	cout.tie(nullptr);

using namespace std;

typedef __int128 i128;
typedef long long ll;
typedef pair<int, int> PII;

const int N = 2e5 + 10;
int m, n, u, v, vis[N];
queue<int> q;
vector<int> g[N];

template <typename T>

inline T read() {
	T sum = 0, fl = 1;
	char ch = getchar();
	for (; !isdigit(ch); ch = getchar())
		if (ch == '-') fl = -1;
	for (; isdigit(ch); ch = getchar()) sum = sum * 10 + ch - '0';
	return sum * fl;
}

template <typename T>

inline void write(T x) {
	if (x < 0) {
		putchar('-'), write<T>(-x);
		return;
	}
	static T sta[35];
	int top = 0;
	do { sta[top++] = x % 10, x /= 10; } while (x);
	while (top) putchar(sta[--top] + 48);
}

void bfs() {
	q.push(1), vis[1] = 1;
	while (q.size()) {
		int f = q.front();
		q.pop();
		for (auto u : g[f]) {
			if (u == 1) {
				write<int>(vis[f]);
				return;
			}
			if (!vis[u]) vis[u] = vis[f] + 1, q.push(u);
		}
	}
	putchar('-'), putchar('1');
}

int main() {
	n = read<int>(), m = read<int>();
	FOR(i, 1, m) u = read<int>(), v = read<int>(), g[u].push_back(v);
	bfs();
	return 0;
}
```

---

ACCode（dfs）：

```cpp
/*Code by Leo2011*/
#include <bits/stdc++.h>

#define INF 0x3f3f3f3f
#define EPS 1e-8
#define FOR(i, l, r) for (int(i) = (l); (i) <= (r); ++(i))
#define log printf
#define IOS                      \
	ios::sync_with_stdio(false); \
	cin.tie(nullptr);            \
	cout.tie(nullptr);

using namespace std;

typedef __int128 i128;
typedef long long ll;
typedef pair<int, int> PII;

const int N = 2e5 + 10;
int m, n, u, v, ans = INF, vis[N];
queue<int> q;
vector<int> g[N];

template <typename T>

inline T read() {
	T sum = 0, fl = 1;
	char ch = getchar();
	for (; !isdigit(ch); ch = getchar())
		if (ch == '-') fl = -1;
	for (; isdigit(ch); ch = getchar()) sum = sum * 10 + ch - '0';
	return sum * fl;
}

template <typename T>

inline void write(T x) {
	if (x < 0) {
		putchar('-'), write<T>(-x);
		return;
	}
	static T sta[35];
	int top = 0;
	do { sta[top++] = x % 10, x /= 10; } while (x);
	while (top) putchar(sta[--top] + 48);
}

void dfs(int u) {
	vis[1] = 1;
	if (g[u].empty()) return;
	for (auto i : g[u]) {
		if (i == 1) {
			ans = min(ans, vis[u]);
			return;
		}
		if (!vis[i]) vis[i] = vis[u] + 1, dfs(i);
	}
}

int main() {
	n = read<int>(), m = read<int>();
	FOR(i, 1, m) u = read<int>(), v = read<int>(), g[u].push_back(v);
	dfs(1);
	write<int>(ans == INF ? -1 : ans);
	return 0;
}
```

理解万岁！