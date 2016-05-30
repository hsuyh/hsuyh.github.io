---
layout: post
title: Dynamic Programming: 以費波那契數列（Fibonacci）為例
---

最近看到有人分享他自己到_[日本line公司的經驗](http://wangyung.blogspot.tw/2016/05/blog-post.html)_

題目要他解一個_[費波那契數列的問題](https://zh.wikipedia.org/wiki/斐波那契数列)_，但是數字非常大，用遞迴一定解不出來，必須使用dynamic programming來解。
看到這個我很疑惑，想到解費氏數列，一定是用遞迴來解，我記得是一個很典型的例子，自己好像沒想過有這個問題，
而且dynamic programming 這個東西我更是忘得一乾二淨...

於是我自己寫了一個遞迴來解費氏數列，以c來寫

```c
unsigned long fibo(int a){
  if (a==1 || a==2)
    return 1;
  else
    return (fibo(a-1) + fibo(a-2));
}
```

我自己測了之後，發現要找第四十幾後，都需要一段時間才有結果，要找第五十個時候，答案就出不來了...

所以只好去研究 Dynamic Programming。
>Dynamic Programming就是去把一個問題分成許多小問題，再去解決每一個小問題。當每個小問題的答案不太一樣時候，其實這時候我們解決這些小問題就等於是解決遞迴問題。但是當其中有很多問題是有一樣的答案時，我們就可以儲存這些答案，減少處理的時間。




參考資料：
1. _[演算法筆記 Dynaimic Programming](http://www.csie.ntnu.edu.tw/~u91029/DynamicProgramming.html#1)_
2. _[Algorithms](http://algorithms.tutorialhorizon.com/introduction-to-dynamic-programming-fibonacci-series/)_
