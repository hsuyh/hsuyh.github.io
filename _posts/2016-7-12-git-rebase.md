---
layout: post
title: git rebase - 修改commit messages 筆記
---

之前第一次參與open source 專案，很開心的提交了自己的程式碼，但其他開發者就提醒我，
一個好的專案應該有乾淨的commit log，
我看了自己的pull request，才發現我的commit message 有夠亂，這樣子的確會造成他人的困擾，因此寫這篇做個筆記一下。

我的程式碼跟commit message 都已經push出去了，
這時候如果你要修改commit message，有以下方法可以達成。

>溫馨提醒：第一次嘗試的人，強烈建議你先自己開一個branch來玩看看

如果你只是想要修改上一個commit，可以用下面這個指令：

```
git commit --amend
```
你就可以像在vim底下編輯一下，直接修改你上一個 commit message。


## 修改多個commit messages

不過一般情況下，我們需要整理多個commit message的時候，就有以下兩種方法：


```
git rebase -i HEAD~3
```
這裡的3可以換成任何數字，意思是你要更改最近的幾個commit messages。


```
git rebase -i commit version
```
這裡的 commit version可以透過git log 查看你的commit，通常commit 版本都會是一長串亂碼，
只需要複製前七碼就可以辨認為你的commit version，
這個指令可以去更改你的commit 以及 commit message。

今天我打了 _＄git rebase -i HEAD~5_
![git](/images/rebase1.png)
你可以看到下面commands部分他寫出你可以做什麼動作。


### 編輯其中一個message - reword
如果你今天要編輯某一個commit message，
把pick 修改成r：

```
r 3adf8be “Your commit message”
```
存擋後他會導到vim模式下，你可以對你的commit message 進行編輯。
再次存擋後，你可以利用git log，就可以發現commit message已經更改成功。


### 編輯其中一個message - edit

如果你今天要編輯某一個commit message，
把pick 修改成e：

```
e 3adf8be "Your commit message"
```

儲存完畢後跳出來，再輸入

```
git commit --amend
```

在vim下，對你的commit message 進行修改

```
git rebase --continue
```

你再去查看log，就可以發現commit message 已經更改成功。


### 合併 commit message - squash

如果你今天你想要把某兩個commit合成一個commit，你就可以使用 squash，
把pick 修改成s：

```
s 3adf8be "Your commit message"
```
![git squash](/images/rebase2.png)

之後他會讓你更改這兩個commit messages，然後再幫你將他們合併。
![git squash](/images/squash1.png)
再看log 你會發現他們確實被合併了。
![git squash2](/images/squash2.png)


### 合併 commit message - fixup

跟squash一樣，他會幫你合併多個commit message，但是他會直接幫你刪掉commit messages，
只留下第一個commit的message。

把pick 修改成f：

```
f 3adf8be "Your commit message"
```

### 刪除 commit

這個動作不只刪掉你的commit message，他連妳這個commit所更改的程式碼都一起刪掉，
你只要將整排pick都刪掉，這個commit就被你刪掉了。

![git delete](/images/git delete1.png)
![git delete2](/images/git delete2.png)
