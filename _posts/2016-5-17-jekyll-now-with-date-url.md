---
layout: post
title: 如何更改 jekyll-now 的url
---

原本[jekyll-now](https://github.com/barryclark/jekyll-now)專案中，你的每篇post的url預設都會是這樣的形式：
_[yourname.github.io/post's title]()_

要是我希望每篇貼文的url可以長得像
_[yourname.github.io/posts/post's title]()_

可以到_config.yml裡面找到設定permalink這行，

```ruby
permalink: /:title/
```
修改permalink的程式碼:

```ruby
permalink: /posts/:title/
```


要是想改成
_[yourname.github.io/posts/year/month/day/post's title]()_

可以修改成

```ruby
permalink: /posts/:year/:month/:day/:title/
```
