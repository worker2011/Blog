---
type: about
update: 2023/12/10/22:45:40
---
Winning isn't  everything, but wanting it is. 获胜并不能代表一切，而求胜心则可以。

------------

此人的各大OJ账号:

- AcWing：[https://www.acwing.com/user/myspace/index/276481/](https://www.acwing.com/user/myspace/index/276481/)

- Hydro：[https://hydro.ac/user/10699](https://hydro.ac/user/10699)

- Open Judge：[http://openjudge.cn/user/1137680/](http://openjudge.cn/user/1137680/)

- 洛谷：就是这个（[顺便推广一下我的博客站](https://www.luogu.com.cn/blog/wonderland-lover/)）

- 一本通在线评测：[http://ybt.ssoier.cn:8088/userinfo.php?name=Leo](http://ybt.ssoier.cn:8088/userinfo.php?name=Leo)

- CodeForces：[![Codeforces Rating of @Leo2011](https://cfrating.baoshuo.dev/rating?username=Leo2011&style=for-the-badge)](https://codeforces.com/profile/Leo2011)

- AtCoder：[![AtCoder Rating of @Leo2011](https://atrating.baoshuo.dev/rating?username=Leo2011&style=for-the-badge)](https://atcoder.jp/users/Leo2011)

- UVA：[https://onlinejudge.org/index.php?option=com_comprofiler&Itemid=3](https://onlinejudge.org/index.php?option=com_comprofiler&Itemid=3)

- SPOJ：Leo2011

- 最后 ~~无耻~~的推广一下我的[博客](https://worker2011.github.io/)
------------

该用户大事记：
1. 2023年6月，首次GESP的C++4级认证，也是第一次参加CCF系比赛/考级（因可能的压分59QwQ）。
2. 2023年9月16日，第1次参加CSP-J/S，第一轮J得74.5分稳过（也是稳稳的[全国一等](https://cdn.luogu.com.cn/upload/image_hosting/m34ty59n.png)），S得45.5分，差GD分数线1分（[全国二等](https://cdn.luogu.com.cn/upload/image_hosting/wm92qljg.png)都没过CAO）……
3. 2023年9月23日，再战GESP的C++4级，69[通过](https://cdn.luogu.com.cn/upload/image_hosting/1kavruhy.png)！

4. 2023年10月21日，参加pj比赛，就会AB两题还全炸了……啥奖没有QwQ

------------

记2023年8月14日发生于Hydro的1个bug

```cpp
#include <bits/stdc++.h>

using namespace std;

const int N = 110, dx[4] = {-1, 1, 0, 0}, dy[4] = {0, 0, -1, 1};
int n, m, mx, mp[N][N], dp[N][N];

void dfs(int x, int y, int depth) {
	if (x < 1 || x > n || y < 1 || y > m)
		return;
	if (dp[x][y] >= depth)
		return;
	dp[x][y] = depth;
	mx = max(mx, depth);
	for (int i = 0;i < 4;i++) {
		int nowx = x + dx[i], nowy = y + dy[i];
		if (mp[nowx][nowy] < mp[x][y])
			dfs(nowx, nowy, depth + 1);
	}
}

int main() {
	scanf("%d%d", &n, &m);
	for (int i = 1;i <= n;i++) {
		for (int j = 1;j <= m;j++) {
			scanf("%d", &mp[i][j]);
		}
	}
	for (int i = 1;i <= n;i++) {
		for (int j = 1;j <= m;j++) {
			dfs(i, j, 1);
		}
	}
	printf("%d\n", mx);
	return 0;
}
```

结果：![](https://cdn.luogu.com.cn/upload/image_hosting/lqky290h.png)

```cpp
#include <bits/stdc++.h>

using namespace std;

const int N = 110, dx[4] = {-1, 1, 0, 0}, dy[4] = {0, 0, -1, 1};
int n, m, mx, mp[N][N], dp[N][N];

void dfs(int x, int y, int depth) {
	if (x < 1 || x > n || y < 1 || y > m) {
		return;
	}
	if (dp[x][y] >= depth) {
		return;
	}
	dp[x][y] = depth;
	if (mx < depth)
		mx = depth;  // 注意看，我把max函数拆开了
	for (int i = 0;i < 4;i++) {
		int nowx = x + dx[i], nowy = y + dy[i];
		if (mp[nowx][nowy] < mp[x][y]) {
			dfs(nowx, nowy, depth + 1);
		}
	}
}

int main() {
	scanf("%d%d", &n, &m);
	for (int i = 1;i <= n;i++) {
		for (int j = 1;j <= m;j++) {
			scanf("%d", &mp[i][j]);
		}
	}
	for (int i = 1;i <= n;i++) {
		for (int j = 1;j <= m;j++) {
			dfs(i, j, 1);
		}
	}
	printf("%d\n", mx);
	return 0;
}
```

结果：![](https://cdn.luogu.com.cn/upload/image_hosting/a7fp36rt.png)

该用户：CAO，TMD老子再也不用什么STL啥的内置函数了……


---

第二天

`priority_queue<int> a;`

The End.
