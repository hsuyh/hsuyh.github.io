---
layout: post
title: Dynamic Programming: 以費波那契數列（Fibonacci）為例
---

最近看到有人分享他自己到_[日本line公司的經驗](http://wangyung.blogspot.tw/2016/05/blog-post.html)_

題目要他解一個_[費波那契數列的問題](https://zh.wikipedia.org/wiki/斐波那契数列)_，但是數字非常大，用遞迴一定解不出來，必須使用dynamic programming來解。
看到這個我很疑惑，想到解費氏數列，一定是用遞迴來解，我記得是一個很典型的例子，自己沒去思考過有這個問題，
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
>Dynamic Programming包含兩部分。
1. Recursion: 就是去把一個問題分成許多小問題，再去解決每一個小問題。
2. Memoization: 當其中很多小問題是有一樣的答案時，我們就可以儲存這些答案，減少處理的時間。

對於費氏數列來說，如果我們只處理遞迴的話，無形中我們就做了很多重複的運算，透過儲存已經計算過的檔案，我們可以減少很多運算時間，但是也會需要額外的記憶體空間來儲存。

Dynamic Programming有以下兩種方法：
1. Bottom-Up：由最小子問題開始解決，逐步累積上去。
2. Top-Down：由最上層開始，以遞迴方式不斷往下做。



Bottom-Up 會由最小的子問題開始計算，所以程式碼只需要幾個迴圈，缺點就是她需要計算所有可能問題。
```c
void fibo_BottomUp(int a, unsigned long* ptr){

  ptr[1] = 1;
  ptr[2] = 1;

  if(a>3)
  {
    for(int i=3; i<=a; i++)
    {
      ptr[i] = ptr[i-1] + ptr[i-2];
    }
  }
}
```
Top-Down  的遞迴結構會強迫從最小問題開始做，我們不必計較計算順序，且不需要去計算所有可能性。
缺點就是它採用遞迴結構，需要不斷呼叫函式，執行效率較差。
```c
unsigned long fibo_TopDown(int a, unsigned long* ptr){
  if(a==1)
  {
    ptr[1]=1;
    return ptr[1];
  }
  else if(a==2)
  {
    ptr[2]=1;
    return ptr[2];
  }
  else
  {
    if(ptr[a]!=0)
    {
      return ptr[a];
    }
    else
    {
      ptr[a] = fibo_TopDown(a-1, ptr) + fibo_TopDown(a-2, ptr);
      return ptr[a];
    }
  }
}
```


參考資料：
1. _[演算法筆記 Dynaimic Programming](http://www.csie.ntnu.edu.tw/~u91029/DynamicProgramming.html#1)_
2. _[Algorithms](http://algorithms.tutorialhorizon.com/introduction-to-dynamic-programming-fibonacci-series/)_
