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
{% image https://i.mituw.com/imgs/2026/02/19/c3a65654416738af.png UUZ~ fancybox:true ratio:3142/1944 %}
```

{% box 效果 %}
{% image https://i.mituw.com/imgs/2026/02/19/c3a65654416738af.png UUZ~ fancybox:true ratio:3142/1944 %}
{% endbox %}

### 人工优化显示效果
对于宽度小而高度大的图片，在宽屏显示器上的显示效果很差（占用大量篇幅），可以通过限定 `width` 和 `padding` 的大小来让一张图片在不同的设备上都有较好的显示效果。
```md 样例
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true width:250px padding:15px ratio:1440/2560 %}
```
{% box 良好的显示 color:green %}
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true width:250px padding:15px ratio:1440/2560 %}
{% endbox %}

{% folding 未优化的显示 color:red %}
{% image https://i.mituw.com/imgs/2026/02/14/a775beeb61b2bd63.webp fancybox:true ratio:1440/2560 %}
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

## Poetry
横排版的诗词。

```md 格式
{% poetry [title] [author:xxx] [footer:xxx] %}
正文
{% endpoetry %}
```

```md 样例
{% poetry 游山西村 author:陆游 footer:诗词节选 %}
莫笑农家腊酒浑，丰年留客足鸡豚。
**山重水复疑无路，柳暗花明又一村。**
箫鼓追随春社近，衣冠简朴古风存。
从今若许闲乘月，拄杖无时夜叩门。
{% endpoetry %}
```

{% box 效果 %}
{% poetry 游山西村 author:陆游 footer:诗词节选 %}
莫笑农家腊酒浑，丰年留客足鸡豚。
**山重水复疑无路，柳暗花明又一村。**
箫鼓追随春社近，衣冠简朴古风存。  
从今若许闲乘月，拄杖无时夜叩门。
{% endpoetry %}
{% endbox %}

## Paper
横排版的文字。

```md 样例
{% paper style:underline title:文言文 author:诸葛亮 date:三国 footer:节选 %}
<!-- line left -->
出师表
<!-- paragraph -->
先帝创业未半而中道崩殂，今天下三分，益州疲弊，此诚危急存亡之秋也。然侍卫之臣不懈于内，忠志之士忘身于外者，盖追先帝之殊遇，欲报之于陛下也。诚宜开张圣听，以光先帝遗德，恢弘志士之气，不宜妄自菲薄，引喻失义，以塞忠谏之路也。
<!-- line right -->
后出师表
<!-- paragraph -->
先帝深虑汉、贼不两立，王业不偏安，故托臣以讨贼也。以先帝之明，量臣之才，固知臣伐贼，才弱敌强也。然不伐贼，王业亦亡。惟坐而待亡，孰与伐之？是故托臣而弗疑也。
{% endpaper %}
```

```yaml 可选参数
style: underline/无 # 是否带下划线
title: # 标题
author: # 作者
date: # 日期
footer: # 页脚信息
```

```md 正文中
<!-- section 小节标题 -->
小节标题，居中显示
<!-- paragraph -->
段落，首行缩进两个字符
<!-- line left -->
段落左对齐
<!-- line right -->
段落右对齐
```


{% paper style:underline title:文言文 author:诸葛亮 date:三国 footer:节选 %}
<!-- line left -->
出师表
<!-- paragraph -->
先帝创业未半而中道崩殂，今天下三分，益州疲弊，此诚危急存亡之秋也。然侍卫之臣不懈于内，忠志之士忘身于外者，盖追先帝之殊遇，欲报之于陛下也。诚宜开张圣听，以光先帝遗德，恢弘志士之气，不宜妄自菲薄，引喻失义，以塞忠谏之路也。
<!-- line right -->
后出师表
<!-- paragraph -->
先帝深虑汉、贼不两立，王业不偏安，故托臣以讨贼也。以先帝之明，量臣之才，固知臣伐贼，才弱敌强也。然不伐贼，王业亦亡。惟坐而待亡，孰与伐之？是故托臣而弗疑也。
{% endpaper %}

{% blur 这个效果就不框起来了，因为框起来会错位（溜 %}

## Reel
竖排版的文字。  
```md 格式
{% reel [title] [author:xxx] [date:xxx] [footer:xxx] %}
正文
{% endreel %}
```

```md 样例
{% reel 蜀道难 author:李白 date:唐 footer:节选 %}
噫吁嚱，危乎高哉！  
蜀道之难，难于上青天！  
蚕丛及鱼凫，开国何茫然！  
尔来四万八千岁，不与秦塞通人烟。  
西当太白有鸟道，可以横绝峨眉巅。  
地崩山摧壮士死，然后天梯石栈相钩连。  
上有六龙回日之高标，下有冲波逆折之回川。  
黄鹤之飞尚不得过，猿猱欲度愁攀援。  
青泥何盘盘，百步九折萦岩峦。  
扪参历井仰胁息，以手抚膺坐长叹。  
{% endreel %}
```

{% reel 蜀道难 author:李白 date:唐 footer:节选 %}
噫吁嚱，危乎高哉！  
蜀道之难，难于上青天！  
蚕丛及鱼凫，开国何茫然！  
尔来四万八千岁，不与秦塞通人烟。  
西当太白有鸟道，可以横绝峨眉巅。  
地崩山摧壮士死，然后天梯石栈相钩连。  
上有六龙回日之高标，下有冲波逆折之回川。  
黄鹤之飞尚不得过，猿猱欲度愁攀援。  
青泥何盘盘，百步九折萦岩峦。  
扪参历井仰胁息，以手抚膺坐长叹。  
{% endreel %}

## Note
Box 的特例。
```md 格式
{% note [title] content [color:color] %}
```

```md 样例
{% note 这是 一个 Note 块。 color:green %}
```

{% note 这是 一个 Note 块。 color:green %}

{% note 注&nbsp;意 如果标题中出现空格，请用 `&nbsp;` 来代替。 color:yellow %}

{% note 颜色 `color` 可设置为 red、orange、amber、yellow、green、cyan、blue、purple、light、dark、warning、error 几种取值。 %}

## Link
链接卡片。
```md 格式
{% link href [title] [icon:src] [desc:true/false] %}
```
```yaml 参数含义
href: 链接
title: 可选，手动设置标题（为空时会自动抓取页面标题）
icon: 可选，手动设置图标（为空时会自动抓取页面图标）
desc: 可选，是否显示摘要描述，为 true 时将会显示页面描述
```

> 随着网站流量的增加，使用主题默认的 API 很可能会导致流量超限，推荐使用自部署的 API 抓取网站信息。参考下方仓库的 README 。

{% link https://github.com/xaoxuu/site-info-api GitHub - xaoxuu/site-info-api icon:https://api.iconify.design/mdi:github.svg %}

## OKR
Objectives and Key Results.   
```md 样例
{% okr o1 %}

2077 年的目标：活到 2078 年。

<!-- okr kr1 percent:100 -->
{% okr o1 %}

2077 年的目标：活到 2078 年。

<!-- okr kr1 percent:100 -->
这是 KR1：
- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:90 status:off_track -->
这是 KR2，做不完了，延期吧。
{% tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endtabs %}

<!-- okr kr3 percent:-25 status:unfinished -->
完成前置准备工作：
{% checkbox 爱素大学习 %}
{% checkbox 希海大学习 %}
{% checkbox 花冠大学习 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% image https://res.xaox.cc/gh/cdn-x/wiki@main/stellar/icon.svg height:64px 支持嵌套插入图片等其它简单组件 ratio:512/512 %}

<!-- okr kr-5 status:invalid percent:10 -->
这是我自己增加的标签

{% endokr %}
```

{% okr o1 %}

2077 年的目标：活到 2078 年。

<!-- okr kr1 percent:100 -->
这是 KR1：
- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:90 status:off_track -->
这是 KR2，做不完了，延期吧。
{% tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endtabs %}

<!-- okr kr3 percent:-25 status:unfinished -->
完成前置准备工作：
{% checkbox 爱素大学习 %}
{% checkbox 希海大学习 %}
{% checkbox 花冠大学习 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% image https://res.xaox.cc/gh/cdn-x/wiki@main/stellar/icon.svg height:64px 支持嵌套插入图片等其它简单组件 ratio:512/512 %}

<!-- okr kr-5 status:invalid percent:10 -->
这是我自己增加的标签

{% endokr %}

## Copy
单行可复制文字。
```md 样例
{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy git:https xaoxuu.com/hexo-theme-stellar prefix:HTTPS %}
{% copy git:ssh xaoxuu.com/hexo-theme-stellar prefix:SSH %}
{% copy git:gh xaoxuu.com/hexo-theme-stellar %}
```

{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy git:https xaoxuu.com/hexo-theme-stellar prefix:HTTPS %}
{% copy git:ssh SamuFlore/BUAA_OOPre_2025
 prefix:SSH %}
{% copy git:gh SamuFlore/BUAA_OOPre_2025 %}

{% box 注意 %}
输入 `git:xxx` 并给出仓库名即可自动生成链接。
{% endbox %}

## Radio
单选框。
```md 样例
{% radio 没有勾选的单选框 %}
{% radio checked:true 已勾选的单选框 %}
{% radio checked:true color:purple 带颜色的单选框 %}
```
{% box 效果 %}
{% radio 没有勾选的单选框 %}
{% radio checked:true 已勾选的单选框 %}
{% radio checked:true color:purple 带颜色的单选框 %}
{% endbox %}

## Checkbox
复选框。
```md 样例
{% checkbox 普通的没有勾选的复选框 %}
{% checkbox checked:true 普通的已勾选的复选框 %}
{% checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}
```
{% box 效果 %}
{% checkbox 普通的没有勾选的复选框 %}
{% checkbox checked:true 普通的已勾选的复选框 %}
{% checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}
{% endbox %}

## Audio
音频标签，这个好。
```md 样例
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}

{% audio netease:1874162498 %}

{% audio type:0 netease:689290264 autoplay:0 %}
```

{% box 效果 %}
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}

{% audio netease:1874162498 %}

{% audio type:0 netease:689290264 autoplay:0 %}
{% endbox %}

{% note 提示 也可以用网易云音乐自己提供的 iframe。 %}

## Video
视频标签，这个更好。
> 支持 bilibili, youtube 和视频外链，可设置最大宽度， bili, yt 均可设置宽度和自动播放。

```md 样例
{% video bilibili:BV1xX4y1F7p6 %}

{% video bilibili:BV1DaRSYiEcE width:80% autoplay:0 %}

{% grid c:2 %}
<!-- cell -->
{% video bilibili:BV1pz4y1Q7T6 %}
<!-- cell -->
{% video bilibili:BV1wF4m1w7fz %}
{% endgrid %}
```

{% video bilibili:BV1xX4y1F7p6 %}

{% video bilibili:BV1DaRSYiEcE width:80% autoplay:0 %}

{% grid c:2 %}
<!-- cell -->
{% video bilibili:BV1pz4y1Q7T6 %}
<!-- cell -->
{% video bilibili:BV1wF4m1w7fz %}
{% endgrid %}

{% blur yt 就不展示了（溜 %}

## 文本修饰标签
```md 样例
- 这是 {% blur 高斯模糊 %} 标签
- 这是 {% psw 密码 %} 标签
- 这是 {% u 下划线 %} 标签
- 这是 {% emp 着重号 %} 标签
- 这是 {% wavy 波浪线 %} 标签
- 这是 {% del 删除线 %} 标签
- 这是 {% sup 上角标 color:red %} 标签
- 这是 {% sub 下角标 %} 标签
- 这是 {% kbd 键盘样式 %} 标签，试一试：{% kbd ⌘ %} + {% kbd D %}
```

{% box 效果 %}
- 这是 {% blur 高斯模糊 %} 标签
- 这是 {% psw 密码 %} 标签
- 这是 {% u 下划线 %} 标签
- 这是 {% emp 着重号 %} 标签
- 这是 {% wavy 波浪线 %} 标签
- 这是 {% del 删除线 %} 标签
- 这是 {% sup 上角标 color:red %} 标签
- 这是 {% sub 下角标 %} 标签
- 这是 {% kbd 键盘样式 %} 标签，试一试：{% kbd ⌘ %} + {% kbd D %}
{% endbox %}

## Box
Box 是许多标签（如 Note）的基础。
```md 格式
{% box [title] [color:color] [child:codeblock/tabs] %}
正文
{% endbox %}
```
### Child 的用法
1. 彩色代码块  
设置 `child:codeblock`，并设置 `color:xxx` 即可实现彩色代码块。
````md 样例
{% box child:codeblock color:green %}
```c 推荐的写法
int i = 1 + 2 + 3;
```
{% endbox %}

{% box child:codeblock color:red %}
```c 不推荐的写法
int i=1+2+3             ;
```
{% endbox %}
````


{% box child:codeblock color:green %}
```c 推荐的写法
int i = 1 + 2 + 3;
```
{% endbox %}

{% box child:codeblock color:red %}
```c 不推荐的写法
int i=1+2+3             ;
```
{% endbox %}

2. 嵌套多段代码块
````md 样例
{% box child:codeblock color:green %}
```c 推荐的写法
int i = 1 + 2 + 3;
```
```c 推荐的写法
int func(int x, int y) {
    //...
}
```
{% endbox %}

````

{% box child:codeblock color:green %}
```c 推荐的写法
int i = 1 + 2 + 3;
```
```c 推荐的写法
int func(int x, int y) {
    //...
}
```
{% endbox %}

3. 嵌套其它标签
比如嵌套一个 Tabs：

{% box child:tabs %}
{% tabs %}
<!-- tab 图文混排 -->
{% image https://res.xaox.cc/posts/20250706162325884.webp-hd 个人电脑作为办公设备时，我们该如何保护隐私？ download:true ratio:1200/600 %}

公司一般都会强制安装安防软件，这些软件要求开机自启动，要求有屏幕录制权限、完全的磁盘访问权限包括相册图库。因此如果使用自己的 MacBook 作为办公设备，必须要把生活区和工作区完全独立开，安装在两个磁盘分区，并且对磁盘分区进行加密。

<!-- tab 示例代码 -->
<script src="https://gist.github.xaox.cc/xaoxuu/c983c958ef0deab819376c231e977ba7.js"></script>
{% endtabs %}
{% endbox %}

知道了这些，可以满足我写作时的绝大多数需求。
