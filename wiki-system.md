---
wiki: next-stellar # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: '文档系统'
date: 
banner: https://i.mituw.com/imgs/2026/02/22/42ae779a61d0ec23.jpg
katex:
topic:
author:
references:
comments:
indexing:
breadcrumb:
leftbar:
rightbar:
h1:
type:
---
## {文档|Wiki} 是什么？
Wiki 是 Stellar 最富特色的一点。

> Stellar 独创了其它 Hexo 主题所没有的 Wiki 文档系统，可以自动找到一个项目的所有文档分页，生成一个目录树，还可以手动指定顺序、标题、分组，而非依赖文件路径、文件名来排序和显示。

{% link https://xaoxuu.com/wiki/stellar/wiki-settings/ 如何使用文档系统 | Stellar icon:https://res.xaox.cc/gh/cdn-x/wiki@main/stellar/icon.svg %}

## 我的经验
作者已经在他的文档中将如何建立 Wiki 文档讲的很清楚了，这里就简单介绍一下我在使用过程中的一些经验。

### 本文贡献者
在每篇文章的末尾显示本文贡献者、编辑本文，并链到 GitHub。  
首先找到 {% u 主题配置文件 %} 的如下字段：
```yaml _config.stellar.yml
contributors:
    edit_this_page: # 从开头开始匹配替换
      '_posts/':  # 如果配置这个，则每篇博文后也会显示贡献者
    js: /js/services/contributors.js
```
在 GitHub 新建一个仓库，用以存放文档的 Markdown 文件，比如仓库名叫做 `MyRepo`。假设文档名为 `MyWiki`。
{% note color:yellow 注意 “文档名”指的是文档配置文件的名字，也就是 `source/_data/wiki/MyWiki.yml`。 %}
在 `edit_this_page` 字段下新增：
{% copy 'wiki/MyWiki/':https://github.com/MyName/MyRepo/blob/main/ %}
把 `MyName` 换成你用户名，`MyWiki` 换成你文档名，`MyRepo` 换成你仓库的名字即可。

### 本文仓库
在 `MyWiki.yml` 中会有这样一项配置：
```yaml MyWiki.yml
repo: # 仓库地址
```
用于填入 GitHub 仓库。这里只需要填入 `用户名/仓库名`，Stellar 会自动为你补全地址。