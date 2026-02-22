---
wiki: next-stellar # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: '起步'
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
## 准备
首先我是从其它主题迁移而来，因此我必须先考虑兼容性问题。按照作者的建议，我首先确认我的环境满足了如下要求：  
```yaml
Hexo: 6.3.0 ~ latest
hexo-cli: 4.3.0 ~ latest
node: 14.17.3 ～ latest LTS # 建议选择 LTS 版本，过高的版本 hexo 还没有进行兼容。
npm: 6.14.13 ~ latest
```

## 安装 Stellar
在博客目录下打开终端，执行：
{% copy npm i hexo-theme-stellar %}
{% note 注意 这将会把主题安装到 `\Blog\node_modules\hexo-theme-stellar` 下。 %}
然后，在 {% u 站点配置文件  %} `_config.yml` 中修改 `theme` 字段为 `theme:stellar`。  

这样，Stellar 就设置为我博客的主题了。  

{% note 更多 更多版本安装及更新，请访问[安装与更新-Stellar](https://xaoxuu.com/wiki/stellar/#%E5%AE%89%E8%A3%85%E4%B8%8E%E6%9B%B4%E6%96%B0)。 %}

## 语法更替
NexT 有自己的标签语法，譬如：  
```markdown
{% note info %}
这是正文
{% endnote %}
```
而这些语法在 Stellar 中是错误的。因此我需要逐个检查之前的博文，删除所有可能引发错误的标签。  

到这一步，执行：  
{% copy hexo cl && hexo g && hexo s %}
通过了编译等过程，在本地见到了使用 Stellar 主题的我的博客。很好，一切正常。

## 字体配置
我选择沿袭先前的设置，用霞鹭文楷作为中文字体。一方面是因为其字库够大，兼有简、繁、和、假名等，另一方面是因为其字形美观，易于阅读。  

{% link https://fonts.google.com/specimen/LXGW+WenKai+Mono+TC?lang=zh_Hant LXGW WenKai Mono TC %}

当然，我选择了等宽字体。{% blur 虽然我没有用它当西文字体。 %}{% blur 你知道的太多了。 %}

怎么配置外部字体呢？Stellar 和 NexT 有所不同。要想引入外部字体，我需要先在{% u 站点配置文件 %}中引入字体来源：  
```yaml _config.yml
inject:
  head:
    - <link href="https://fonts.googleapis.com/css2?family=LXGW+WenKai+Mono+TC&display=swap" rel="stylesheet">
  script:
```
{% note 注意 `inject` 字段可以插入于 `_config.yml` 的任意位置，如果需要引入更多字体，请添加 `head` 字段的内容。 %}

接着，在 {% u 主题配置文件 %} `_config.stellar.yml` 中填写引入的字体名称：
```yaml _config.stellar.yml
style:
    font-family:
        body: '"LXGW WenKai Mono TC", ...'
```
{% box 注意 %}
- 如果没有 `_config.stellar.yml`，可以自行创建。
- 关于字体选择的优先级，我在之前的[一篇博文](https://samuflore.top/posts/ec5f1055/)中提到过。
{% endbox %}
这样，我设置好了字体，看着非常亲切。

## 配置侧边栏
Stellar 的侧边栏默认是没有通往别的页面的按钮的，我计划放 4 个上去，分别是{主页|博客}、文档、留言和友链。  
这块区域叫做{主导航栏|Navbar}，可以自己定义键值对，我的设置是：  
```yaml _config.stellar.yml
# 侧边栏主功能导航菜单
menubar:
  columns: 4 # 一行多少个
  items: # 可按照自己需求增加，符合以下格式即可
    # id: 页面中高亮的 menu_id 
    # theme: 高亮时的颜色，仅 svg 中 fill="currentColor" 时有效
    # icon: 支持 svg/img 标签，可以定义在 icons.yml 文件中，也支持外部图片的 URL
    # title: 标题
    # url: 点击跳转到哪，支持相对路径和绝对路径
     - id: post
       theme: '#77BBDD' 
       icon: solar:bookmark-broken
       title: 博客
       url: /

     - id: wiki
       theme: '#7777AA' 
       icon: solar:emoji-funny-circle-line-duotone
       title: 文档
       url: /wiki/

     - id: guestbook
       theme: '#FFDD88' 
       icon: solar:notebook-bookmark-line-duotone
       title: 留言
       url: /guestbook/

     - id: links
       theme: '#FF8899' 
       icon: solar:hearts-line-duotone
       title: 友链
       url: /links/
```
{% blur 配色略有奥妙，你发现了吗（ %}
{% note 键值对 键：`menu_id`，值：`url`。 %}
这样在左侧边栏就出现了四个按键。定义 icons 的 `icons.yml` 在 `\blog\node_modules\hexo-theme-stellar\_data\icons.yml`。亦可以调用 Iconify 的 API 来使用 svg 图形。
{% box 调用 Iconify API %}
生成 svg 的 url 格式如下：
{% copy https://api.iconify.design/prefix/name.svg %}

其中 `prefix/name` 一处可以在 Iconify 选中心仪的图标，复制其名字得到。
{% endbox %}

### 绑定具体页面
这时候你肯定要问了：
{% quot menu_id 是干什么的？ %}
其实，它只有一个小小的作用，就是让主题知道你正在浏览哪一种页面，根据页面的不同显示不同的内容。以这 4 个按键为例，当我点击某一按键，待页面加载完成之后，这个按键就是{% mark 高亮 %}的。这是因为我在这个页面的 md 文件的 front-matter 中声明了「这个页面的 `menu_id`」，当检测到页面的 `menu_id` 与上述的 `menu_id` 相符时，这个按键就会亮起。譬如：
```md guestbook.md
---
title: 留 言
menu_id: guestbook
---
```

## 创建文章
Stellar 支持给文章设置{封面|cover}，{摘要|description}，{海报|poster}（全图封面卡片）等内容。我可以先写好模板：
```md /blog/scaffolds/post.md
---
title: {{ title }}
date: {{ date }}
tags:
categories:
password:
top:
# 基本信息
description: # excerpt 也可 
# 封面
cover: 
banner: 
poster: # 海报（可选，全图封面卡片）
  topic: 标题上方的小字 # 可选
  headline: 大标题 # 必选
  caption: 标题下方的小字 # 可选
  color: 标题颜色 # 可选
# 插件
katex: 
# 可选
topic: # 专栏 id
author: 
references:
comments: # 设置 false 禁止评论
indexing: # 设置 false 避免被搜索
breadcrumb: # 设置 false 隐藏面包屑导航
leftbar: 
rightbar:
h1: # 设置为 '' 隐藏标题
type: # tech/story
---
```
其中某些选项是需要另外安装插件的。  

{% note 注意 在 Stellar 中，文章的标签在具体的文章页面是不可见的。 %}

这样每次执行 `hexo n` 时就可以减少填写 front-matter 的工作量。  


到这里，Stellar 就大体上配置完成了。再次感叹一下将艺术和审美融入前端工作能做出多么优雅的作品。