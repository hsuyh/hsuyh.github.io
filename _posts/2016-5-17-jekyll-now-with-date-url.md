---
layout: post
title: 如何更改 jekyll-now 的url
---

原本[jekyll-now](https://github.com/barryclark/jekyll-now)專案中，你的每篇post的url預設都會是這樣的形式：
_[yourname.github.io/post's title]()_

要是我希望每篇貼文的url可以長得像
_[yourname.github.io/posts/post's title]()_

可以到_config.yml裡面，
```ruby
permalink: /:title/
```
修改permalink那邊的程式碼:
```ruby
permalink: /posts/:title/
```
