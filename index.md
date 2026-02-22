---
wiki: next-stellar # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: '从 NexT 到 Stellar'
date: 2026-02-18 21:23:43
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
## 序
我为什么换用 Stellar？  
——根据 LeanCloud 发布的[通知](https://docs.leancloud.cn/sdk/announcements/sunset-announcement)，LeanCloud 的生命即将走向尽头。  
{% timeline %}
<!-- node 2026 年 1 月 12 日 -->
- 停止新用户注册
- 停止创建新的应用  
现有存量应用在正式停止服务前，仍可继续正常使用。
<!-- node 2027 年 1 月 12 日 -->
平台将正式关闭所有面向公众的服务，包括应用访问、数据读写、API 调用、控制台使用等。
{% endtimeline %}
我之前一直使用的 Valine 评论系统所依靠的数据库正是 LeanCloud。为了能够继续使用评论系统，我不得不着手将 Valine 迁移到其衍生版本 Waline 上来。
{% link https://waline.js.org/ Waline.js icon:https://waline.js.org/logo.png %}
然而天不遂人意，Waline 所支持的 NexT 版本为 NexT 8 以上，而由于历史原因，NexT 不同版本可能在不同仓库中，导致我当时所用的是 NexT 7 的某个版本，却一直认为自己用的是最新版。  
我对原版的 NexT 主题魔改了很多，若从 NexT 7 升级到 NexT 8，许多改动会失效，于是我决定直接放弃 NexT，转而使用我早就相中的 Stellar！  

第一次见到 Stellar，是从一个叫 Clarity 的 Nuxt 主题那，它吸收了 Stellar 的设计风格。更换博客框架已不现实。不过 Stellar 并不比这位兄弟差，当时我就动了更换主题的念头。
{% link https://github.com/L33Z22L11/blog-v3 GitHub %}
{% link https://blog.zhilu.site/ 纸鹿摸鱼处 icon:https://weavatar.com/avatar/47c0f2e82b76d9b10eb3023df9e02e4e3fdbeaf5b74b842063f207971e7fbe7b?s=160 %}
那么作为上手使用 Stellar 的练习，亦作为我更换主题的记录，这篇 Wiki 诞生了。
