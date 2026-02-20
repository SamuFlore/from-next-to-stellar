---
wiki: next-stellar # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: '标签语法'
date: 
banner: https://i.mituw.com/imgs/2026/02/19/a4954f2727ba5007.png
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
## 使用 Stellar 的标签
Stellar 为我提供了丰富的标签，几乎可以满足一切需求。写下这一篇内容之前，我甚至还没有体验完全部的内容。  
我深知即使写完这一小节，仍会有许多内容无法完全表述，故在此附上作者的文档。
{% link https://xaoxuu.com/wiki/stellar/tag-plugins/express/ 表达类标签组件 %}
{% link https://xaoxuu.com/wiki/stellar/tag-plugins/data/ 数据类标签组件 %}
{% link https://xaoxuu.com/wiki/stellar/tag-plugins/container/ 容器类标签组件 %}
{% blur 所以我就只写一些我感兴趣的标签语法了（ %}
{% note 前排提醒 `[]` 表示可选参数；`xx:xx` 表示键值对参数，其位置无要求；其它参数为必选参数。 %}

## Emoji
```md 格式
{% emoji [source] name [height:xx] %}
```
`source` 定义在 `_config.stellar.yml` 的 `emoji` 字段。
```md 样例
{% emoji blobcat 0_0 %}
```
{% box 效果 %}
{% emoji blobcat 0_0 %}
{% endbox %}

作者的 CDN 提供了一小部分表情的名字可供参考。
{% link https://gcore.jsdelivr.net/gh/cdn-x/emoticons@3.1/blobcat/ cdn-x/emoticons CDN files %}
你说这小玩意到底谁研究的呢怎么这么可爱 {% emoji blobcat attention %}

## Icon
```md 格式
icons.yml 中的图标：{% icon solar:planet-bold-duotone %}
外链图标：{% icon https://api.iconify.design/solar:link-circle-bold.svg %}
指定颜色：{% icon ph:seal-question-fill color:red %}
```
```md 样例
{% icon solar:planet-bold-duotone %}
{% icon https://api.iconify.design/solar:link-circle-bold.svg?color=blue %}
{% icon ph:seal-question-fill color:red %}
```
{% box 效果 %}
{% icon solar:planet-bold-duotone %}
{% icon https://api.iconify.design/solar:link-circle-bold.svg?color=blue %}
{% icon ph:seal-question-fill color:red %}
{% endbox %}

## Mark
```md 样例
支持多彩标记，包括：{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} {% mark 青 color:cyan %} {% mark 蓝 color:blue %} {% mark 紫 color:purple %} {% mark 亮 color:light %} {% mark 暗 color:dark %} {% mark 警告 color:warning %} {% mark 错误 color:error %} 一共 12 种颜色。
```
经过我的实践，其它使用 `color` 指定颜色的标签，大概也只能选择这些颜色（未证实）。

{% box 效果 %}
支持多彩标记，包括：{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} {% mark 青 color:cyan %} {% mark 蓝 color:blue %} {% mark 紫 color:purple %} {% mark 亮 color:light %} {% mark 暗 color:dark %} {% mark 警告 color:warning %} {% mark 错误 color:error %} 一共 12 种颜色。
{% endbox %}

## Hashtag
\# 号标签。
```md 样例
{% hashtag Stellar https://xaoxuu.com/wiki/stellar/ %}
{% hashtag Hexo https://hexo.io/ %}
{% hashtag GitHub https://github.com/SamuFlore/ %}
{% hashtag SamuFlore's&nbsp;Dimension https://samuflore.top color:orange %}
```
如果不指定颜色，则颜色是随机的。

{% box 效果 %}
{% hashtag Stellar https://xaoxuu.com/wiki/stellar/ %}
{% hashtag Hexo https://hexo.io/ %}
{% hashtag GitHub https://github.com/SamuFlore/ %}
{% hashtag SamuFlore's&nbsp;Dimension https://samuflore.top color:orange %}
{% endbox %}

## Image
好用，我再也不想给博文上传本地图片了。
```md 格式
{% image src [description] [download:bool/string] [width:px] [padding:px] [bg:hex] [fancybox:bool/string] %}
```

```yaml 说明
src: 图片地址
description: 图片描述
download: href # 下载地址，设置此值后鼠标放在图片上会显示下载地址，如果下载地址为图片地址，可以设置为 true
width: 200px # 图片宽度
padding: 16px # 图片四周填充宽度
bg: '#ffffff' # 图片区域背景颜色，16进制
fancybox: href # fancybox 放大地址，设置此值后会调用该链接放大，如果放大地址为图片地址，可以设置为 true
```

```md 样例
{% image https://i.mituw.com/imgs/2026/02/19/c3a65654416738af.png UUZ~ fancybox:true %}
```

{% box 效果 %}
{% image https://i.mituw.com/imgs/2026/02/19/c3a65654416738af.png UUZ~ fancybox:true %}
{% endbox %}

### 人工优化显示效果
对于宽度小而高度大的图片，在宽屏显示器上的显示效果很差（占用大量篇幅），可以通过限定 `width` 和 `padding` 的大小来让一张图片在不同的设备上都有较好的显示效果。
```md 样例
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true width:250px padding:15px %}
```
{% box 良好的显示 color:green %}
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true width:250px padding:15px %}
{% endbox %}

{% folding 未优化的显示 color:red %}
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true %}
{% endfolding %}

## Blockquote
Markdown 语法 `> 引用内容` 的升级版。
```md 样例
{% blockquote %}
{なんで「春日影」やったの?!!|为什么要演奏《春日影》？！！}
{% endblockquote %}
```
{% box 效果 %}
{% blockquote %}
{なんで「春日影」やったの?!!|为什么要演奏《春日影》？！！}
{% endblockquote %}
{% endbox %}

## Quot
这是一个神秘的名字，大概是为了避免命中 Hexo 的某些彩蛋。
```md 样例
默认形式：{% quot 你好，世界！ %}
可以自定义符号：{% quot 你好，世界！ icon:hashtag %}
可以作为标题使用（el:h1/h2/h3/h4/h5/h6）：{% quot 你好，世界！ el:h3 %}
使用外部图形（icons.yml）：{% quot 你好，世界！ prefix:solar:planet-bold-duotone %}
使用外部图形（url）：{% quot prefix:https://api.iconify.design/line-md:moon-alt-to-sunny-outline-loop-transition.svg?color=red 你好，世界！ suffix:https://api.iconify.design/solar:list-heart-minimalistic-line-duotone.svg?color=blue %}
```


{% box 效果 %}
{% quot 你好，世界！ %}
{% quot 你好，世界！ icon:hashtag %}
{% quot 你好，世界！ el:h3 %}
{% quot 你好，世界！ prefix:solar:planet-bold-duotone %}
{% quot prefix:https://api.iconify.design/line-md:moon-alt-to-sunny-outline-loop-transition.svg?color=red 你好，世界！ suffix:https://api.iconify.design/solar:list-heart-minimalistic-line-duotone.svg?color=blue %}
{% endbox %}

> 虽然丰富多彩的图标可以使其变得更醒目，但是滥用就会导致文章显得杂乱无章。
