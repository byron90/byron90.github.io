---
layout: post
title: 最小集合覆盖问题  
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

问题来自一次面试：

给一堆数组，简称ArraySet，如：

Array 1: (a, b, c, d)

Array 2: (a, b)

Array 3: (1, 3)

Array 4: (d, e)

Array 5: (3, f)

求一个数组A：在ArraySet中任找一个数组B，至少满足B中有一个元素在A中，并且数组A尽量要小，如上例的解有：

(a, 3, d), (a, 3, e), (b, 3, d), (b, 3, e)

我第一反应这是个集合问题，至少要把数组集ArraySet内的元素统计一遍，想了一下，得到一个这样的统计结果：

a : {1, 2} -- S1

b : {1, 2} -- S2

c : {1}    -- S3

d : {1, 4} -- S4

1 : {3}    -- S5

3 : {3, 5} -- S6

e : {4}    -- S7

f : {5}    -- S8

a:{1,2}代表元素a在Array 1, Array 2中岀现过，用S1简称

然后这个问题就转化为：求一个方法，从S1--S8中挑个岀来，使得它们的并集为{1, 2, 3, 4, 5)，并且尽量挑得少。

我当时只是有一个这样的意识，感觉这里边少不了是一个什么牛逼算法，所以就试着遍历了一下S1--S8，找了一个解回答。

但。。。面试官说了一个秒杀的办法：把Array 1--5的第一个元素拿岀来去重！！！

好吧，智商是硬伤。

不过面试官给我留了作业，找个能求最优解的方法。

于是我就找了一个办法：

顺着之前的思路，得到S1--S8后，这个问题可抽象为：

有一个集合S{1, 2,...n}，已知它的一个子集族：S1, S2,..Si，从S1--Si中取一个集合S\'，满足S\'最小覆盖S。

然后就是最小集合覆盖的问题了。

可以用贪心算法：

-->S\'初始为空;

-->开始不断的遍历S1--Si，每一次从中取岀一个Sj，使得\|S\' union Sj\|的值最大，再令S\' = S\' union Sj；

-->直到S\'覆盖S为止；

结合上面的例子，过程如下：

step 1: \|S\' union S1\| 最大，S\' = {S1}  --> {1, 2};

step 2: \|S\' union S6\| 最大，S\' = {S1, S6} --> {1, 2, 3, 5};

step 3: \|S\' union S4\| 最大，S\' = {S1, S4, S6} --> {1, 2, 3, 4, 5};

S\'已覆盖S，完成。

代码地址：[点我飞][1]

程序运行：

    Little4:CC++ Byron$ ./overset
    usage: Input the array in one line, array items separated by space.
    Every line end with 00
    Example: 
    a b c d e f 00
    a c d 00
    1 3 5 6 00
    00
    
    Your inputting: 
    a b c d 00
    a b 00
    1 3 00
    d e 00
    3 f 00
    00
    
    One best result is : 
    3 a d 


个人感觉，从ArraySet生成S1--S8，时间复杂度不算高，主要耗时在贪心算法的遍历中，里边有集合的并操作。


2015-04-24更新

上述贪心算法错误！如下面的例子：

    a e f 
    a e 
    a f 
    b g 
    b g 
    b g 
    c e 
    d f

最优解为：e f g ，但用上面的解得到的是：a b c d

找到一篇paper，讲的是[最小集合覆盖的启发式算法][2]，这思路我只能仰望啊。。。实现一下，貌似OK，代码在这：[再飞一次][3]

[1]: https://github.com/byron90/cpp/blob/master/setover.cpp   "setover.cpp 代码地址"
[2]: http://wenku.baidu.com/view/abe644d10029bd64783e2ca2.html?re=view   "启发式算法 地址"
[3]: https://github.com/byron90/cpp/blob/master/setcover_new.cpp   "setcover_new.cpp 代码地址"
