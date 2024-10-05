---
title: Markdown 测试
date: 2024-08-31 17:34:08
tags: 测试
categories: 测试
sticky: 8
expires: 2024-08-31 00:00:00
thumbnail: /images/bg.jpg
---

~~你应该需要输入“123456”才能查看这篇文章~~，而且这篇文章应该是所有三十多篇文章中的第三篇。

I AK IOI!

**I AK IOI!**

~~I AK IOI!~~

*I AK IOI!*

<!--more-->

上面会被当做概要部分，下面会被一个“阅读全文”代替。

# I AK IOI!
## I AK IOI!
### I AK IOI!
#### I AK IOI!
##### I AK IOI!
###### I AK IOI!

1. I AK IOI!

2. I AK IOI!

- I AK IOI!

* I AK IOI!



![测试图片一号](https://s2.loli.net/2024/07/23/oQdXu1b6DlRIhfw.png)

![测试图片二号](/images/bg.jpg)

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
// 这是一个代码块
```

以上是 Markdown 语法。

---

$2 ^ {10} = 1024$

---

{% notel blue 提示 %}
换行测试
换行测试
换行测试

大标签测试
{% endnotel %}

{% note success  %}
success 提示块标签
{% endnote %}

{% note red fa-bolt%}
自定义提示块标签
{% endnote %}

普通 {% btn 按钮:: / %}

{% folding blue::Folding 测试： 点击查看更多 %}
啊啊啊啊啊……
{% endfolding %}

{% tabs First unique name %}
<!-- tab First Tab-->
**This is Tab 1.**
<!-- endtab -->
 
<!-- tab Second Tab-->
**This is Tab 2.**
 
This is Tab 2.
<!-- endtab -->
 
<!-- tab Third Tab-->
**This is Tab 3.**
 
This is Tab 3.
 
This is Tab 3.
<!-- endtab -->
{% endtabs %}

```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

以上是[Hexo-Theme-Redefine](https://redefine-docs.ohevan.com/)的一些独有功能。

---

其它：

{% spoiler 测试文本 %}
内容
{% endspoiler %}

测试结论：折叠类内容不支持嵌套，其它一切正常。
