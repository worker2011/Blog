---
title: "C艹好东西系列3——__int128和short"
categories: "C艹好东西系列"
---

### 先说说__int128
高精度大家都认识吧？

但是，高精度这货是真滴长……

于是，人们又发明出了一个东西 \__int128！

\__int128（注意前面有2个下划线）嘛，把特点写脸上了：占用128位，也就是16个字节。储存范围，自然也是占用64位的long long的2倍。换算一下，能存三十多近四十位。基本上可以代替部分高精度了。

那__int128这么NB，咋就不能被广泛使用呢（好多教材没教这个对不）？

因为它缺陷也很多：

1. 不通用。\__int128并没有在任何一个C艹标准中严格定义 ，所以目前它只是GCC系列编译器的专属（NOI Linux恰好也用的是GCC，所以__int128可用。然鹅，使用Visual Studio的同志们，你们用的编译器一般是MSVC，是不支持的）。目前测试，只在Linux系统下能够正常使用（好在大部分地区比赛、评测均已切换至NOI Linux 2.0了）。
2. 不方便。\__{int128}目前看来是不支持直接读入、输出的。管你是cin、cout、scanf还是printf，都甭想输入一个__int128类型的数据。于是它输入得用sring输入字符后\times 10 +尾数，输出得数位分解。
3. 空间大，速度慢。 \__int128占用了16个字节来存，MLE的风险显著增加。空间大速度还慢。你想啊，人家int才32位，64位的CPU一次处理俩；你128位，64位的CPU两次处理1个，不得慢死（TLE风险增加）……

不过，为了让大家多掌握（pian）亿点东（fen）西，下面给出使用\__int128时的基本框架。

{% spoiler Code %}
```cpp
#include <bits/stdc++.h>

#define log printf

using namespace std;

__int128 n;

__int128 reader() {
	__int128 x = 0; // 虽然限制那么多，但咱赋个值总还是可以的吧…… 
    int w = 0; 
    char ch;
    while (!isdigit(ch)) { 
    	w |= ch == '-'; ch = getchar(); 
    }
    while (isdigit(ch)) 
    	x = (x << 3) + (x << 1) + (ch ^ 48), ch = getchar();
    return w ? -x : x;
}

void output(__int128 x) {
    if (x < 0) {
        putchar('-');
        x *= -1;
    }
	if (x > 9)
		output(x / 10);
	putchar(x % 10 + '0');  // 众所周知这货只能搞四则运算，输出还请数位分解一下（其实就是快读快写）
}

int main() {  // 你变量全用__int128我也不拦着你，但永远记住main函数不开int（好吧用signed也行）会CE的哈 
	n = reader();
	// 请自行操作
	output(n);
	return 0; 
}
```
{% endspoiler %}

---

### 再讲讲short

说了这么半天慢的太吓人的\__int128，那有木有一个特快的，比如说16位2个字节的哪种？
还真有，而且这个槽点就没那么多了。它就是——short！

short这玩意儿可比__int128强多了。它是通用的，也是可以直接读入、输出的（scanf和printf统一用“%hd”）。

那为啥它用的也不多呢？

因为它太省内存了，你说它就 $2^{15} - 1$ (不到4万）的存储范围能存个啥？
