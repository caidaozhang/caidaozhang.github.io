---
layout: post
title: 开篇
---
## 引言
> 最近在看张星星的《CSS世界》，国内研究CSS的前端里很难发现有研究的这么彻底的。值得认真拜读。这个Blog的开始，就拿来记录看书中遇到的问题吧。

## 2.2 中if (button.addEventListener)的条件值

```js
if (button.addEventListener) {
    button.addEventListener("mousedown", function(event) {
        // 此处省略N行
        event.preventDefault();    
    });
}
```
## 问题：
W3school解释：
> If 语句
> 只有当指定条件为 true 时，该语句才会执行代码。

if的条件不是只能当为true时，才执行么？这个button.addEventListener不是为true啊？在console中

```
>button.addEventListener
>ƒ addEventListener() { [native code] }
>typeof(button.addEventListener)
>"function"
>typeof(true)
>"boolean"
```
可以看到button.addEventListener是个function，不是布尔型。
***
## 解答：
已经在该书的[BBS提问](http://bbs.cssworld.cn/forum.php?mod=viewthread&tid=71&page=1&extra=#pid185)。看看有更好的答案出现没？
根据自己的搜索目前找到最好的答案是：<br/>
### 1. [解答1](http://www.jb51.net/article/50197.htm)

在javascript中，哪些值能作为if的条件呢<br/>
1. 布尔变量 true / false<br/>
2. 数字 非0,非undefined /（0或undefined)<br/>
3. 对象 非null /（null或undefined) <br/>
4. 字符串 非空串（"xxx"）/ 空串("")<br/>

此处，if (button.addEventListener) 的条件button.addEventListener是一个function对象，拿来判断这个对象是否存在，如果存在就执行。可以防止JS报错。