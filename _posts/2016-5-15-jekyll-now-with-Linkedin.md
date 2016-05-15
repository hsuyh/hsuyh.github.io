---
layout: post
title: 如何在jekyll-now中加入你的Linkedin Profile
---

今天成功部署[jekyll-now](https://github.com/barryclark/jekyll-now)到github pages上，但是我在新增Linkedin檔案的時候，一直無法成功新增。

在_config.yml之中，footer-links那裡填上自己的linkedin url，但一直被導向找不到這個頁面，後來查到[jekyll-now的issue#288](https://github.com/barryclark/jekyll-now/issues/288)。

底下作者建議他直接在那邊填上你自己的username就可以了。

但其實我疑惑的是，我的username是有中文的，且我真的填下去後還是失敗。

依照這個linkedin 說明中心的[連結](https://www.linkedin.com/help/linkedin/answer/87)的步驟，你必須去開啟你的公開檔案位址。

1. 當你按下齒輪後進入到你的個人資料頁面，
2. 在網頁右邊有一個檔案位址的欄位，你只要按下 `＋輸入自定位址`，在這邊新增你的公開網址，請記下你這邊填的id。
3. 把id填到_config.yml中的Linkedin欄位即可。
