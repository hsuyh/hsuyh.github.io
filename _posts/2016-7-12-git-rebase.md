---
layout: post
title: git rebase 筆記
---

之前第一次參與open source 專案，很開心的提交了自己的程式碼，但其他開發者就提醒我，
一個好的專案應該有乾淨的commit log，
我看了自己的pull request，才發現我的commit message 有夠亂，這樣子的確會造成他人的困擾，因此寫這篇做個筆記一下。

我的程式碼跟commit message 都已經push出去了，
這時候如果你要修改commit message，有以下方法可以達成，


如果你只是想要修改上一個commit，可以用下面這個指令：

```
git commit --amend
```
你就可以像在vim底下編輯一下，直接修改你上一個 commit message。


### 修改多個commit messages

不過一般情況下，我們需要整理多個commit message的時候，就有以下兩種方法：



```c
git rebase -i HEAD~3
```
這裡的3可以換成任何數字，意思是你要更改最近的幾個commit messages。



```c
git rebase -i commit version
```
這裡的 commit version可以透過git log 查看你的commit，通常commit 版本都會是一長串亂碼，
只需要複製前六碼就可以辨認為你的commit version，
這個指令可以去更改你指令的commit 之後的commit message。
