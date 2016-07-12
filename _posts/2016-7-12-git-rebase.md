---
layout: post
title: git rebase 筆記
---

之前第一次參與open source 專案，很開心的提交了自己的程式碼，但其他開發者就提醒我，
一個好的專案應該有乾淨的commit log，
我看了自己的pull request，才發現我的commit message 有夠亂，這樣子的確會造成他人的困擾。

但是我的程式碼跟commit message 都已經push出去了，
這時候如果你要修改commit message，有以下方法可以達成，
因此寫這篇做個筆記一下。

如果你只是

```c
git rebase --amend
```

1. git log 去查



git rebase -i log
git rebase -i HEAD~3
