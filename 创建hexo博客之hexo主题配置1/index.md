# 创建Hexo博客之Hexo主题配置1


## 前言

[Hexo](https://hexo.io/zh-cn/index.html)是一款基于Node.js的静态博客生成器。他可以帮助用户快速、轻松地创建并部署自己的博客网站。

Hexo的主要特征包括以下几点：

1. 快速：Hexo采用了缓存机制和异步渲染技术，生成速度非常快；
2. 简单易用：Hexo的配置非常简单，它支持大量的[主题](https://hexo.io/themes/)和[插件](https://hexo.io/plugins/)，使得用户可以快速打造自己的个性化博客；
3. Markdown支持： Hexo支持使用Markdown语法来编写文章，并且可以直接在命令行界面预览效果；
4. 多平台支持：Hexo可以发布到多种平台，例如：Github Pages、HeroKu以及Netlity等等；
5. 插件丰富：Hexo有大量的插件可以供选择，如SEO优化、社交分享等，可以很大程度上满足用户的各种需求；

总而言之，Hexo是一款非常优秀的博客生成器，它能够让用户快速地创建自己的博客网站，并提供了十分丰富的主题和插件来满足用户的需求。

## 配置

### 语言、网站资料

Hexo博客默认的语言是`en`，支持三种不同的语言，分别是`default(en)`、`zh-CN(简体)`以及`zh-TW(繁体)`，修改博客语言需要到根目录下的`_config.yml`文件中找到`language:`，将值改为`zh-CN`。

```yml
# Site
language: zh-CN
```

修改网站各种资料，例如标题、副标题和邮箱等个人资料，请修改博客根目录的`_config.yml`文件。

```yml
# Site
title: '小陈的博客'
subtitle: '一个想摆烂的代码人'
description: '欢迎来到摆烂的代码世界'
keywords: Blog
author: Chen
language: zh-CN
timezone: ''

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: http://qichenni.github.io
```

### 导航栏设置

**上面是修改的文件是博客根目录下的`_config.yml`文件内容，接下来要修改的内容都是在刚刚创建的`_config.butterfly.yml`文件。**

#### 参数设置

```
nav:
  logo: #image
  display_title: true
  fixed: false # fixed navigation bar(固定导航条)
```

|     参数      |                     解释                      |
| :-----------: | :-------------------------------------------: |
|     logo      | 网站的logo，支持图片，可以直接填入图片的链接  |
| display_title | 是否显示网站标题，true表示显示，false表示关闭 |
|     fixed     |                是否固定状态栏                 |

#### 菜单/目录

主题中的配置文件中的关于菜单/目录都是被注释着的，当我们需要启用的时候，只需要将前面的‘#’号删除即可。
原来的菜单/目录的配置如下：
```yml
Home: / || fas fa-home
Archives: /archives/ || fas fa-archive
Tags: /tags/ || fas fa-tags
Categories: /categories/ || fas fa-folder-open
List||fas fa-list:
  Music: /music/ || fas fa-music
  Movie: /movies/ || fas fa-video
Link: /link/ || fas fa-link
About: /about/ || fas fa-heart
```

但由于我们在这里没有movie和music，因此，我们可以将movie和music删除，更替为link和about。

```yml
# 进入_config.butterfly.yml
menu:
  主页: / || fas fa-home
  时间轴: /archives/ || fas fa-archive
  标签: /tags/ || fas fa-tags
  分类: /categories/ || fas fa-folder-open
  链接||fas fa-list:
    友情链接: /link/ || fas fa-link
    关于我: /about/ || fas fa-heart
```

> 需要注意的是，书写格式必须要必须是`/xxx/`，后面`||`分开，然后写图标名，如果你不想它显示图标，也可以不写图标名，子目录默认是展开的，如果想要隐藏展开，只需要在子目录后加上一`||hide`即可，例如`链接||fas fa-list || hide:`，最后，导航栏的名字可以自行更改。

### 代码设置

**注意**：代码块中的所有功能只适用于 Hexo 自带的代码渲染，如果使用第三方的渲染器，不一定会有效。

#### 代码高亮样式

butterfly主题支持六种不同的代码高亮样式，分别是：`darker`、`pale night`、`light`、`ocean`、`mac`、`mac light`。

修改代码高亮样式也很简单，只需要我们进入主题配置文件，将代码高亮主题改成自己喜欢的主题即可。

```yml
# 进入_config.butterfly.yml
highlight_theme: mac
```

> darker

![darker](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/darker.png)

> pale night

![pale night](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/pale%20night.png)

> light

![light](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/light.png)

> ocean

![ocean](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/ocean.png)

> mac

![mac](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/mac.png)

> mac light

![mac light](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/mac%20light.png)

如果你不喜欢或者不需要代码高亮，你也可以将`highlight_theme`改为`false`，这样的效果如下：

![false](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/false.png)

最后，如果以上这几款都不能满足你，你也可以自定义代码高亮，主题作者也给出了自定义代码高亮主题的教程，点击[此链接](https://butterfly.js.org/posts/b37b5fe3/)跳转过去吧。

#### 代码复制

顾名思义，就是设置代码是否可以被复制的一项功能，这项功能默认是开启的，如果你不希望代码能够被复制，可以在主题配置文件，也就是`_config.butterfly.yml`中找到`highlight_copy: true`改为`highlight_copy: false`即可。

#### 代码框展开/关闭

在默认的情况下，代码框是自动展开的，如果你不希望代码框默认是展开的，可以去主题配置文件，也就是`_config.butterfly.yml`中找到`highlight_shrink:`，将其属性从`false`改成`true`，当我们将这一属性改为`true`之后，代码框就会默认不展开，需要我们点击代码框上的‘>’来展开。

作者也针对这一属性给出了三个属性值，第一个是`true`，当我们选择这个属性值的时候，全部代码框是不展开的，需要点击`>`才能展开；第二个是`false`，当们选择这个属性值的时候，全部代码是展开的，可以点击`>`来关闭代码框；最后一个就是`none`，当我们选择这个属性值的时候，是全部展开的，并且没有`>`按钮来控制开与关。

> 你也可以在post/page页对应的markdown文件front-matter添加highlight_shrink来独立配置。当主题配置文件中的 highlight_shrink 设为true时，可在front-matter添加highlight_shrink: false来单独配置文章展开代码框。当主题配置文件中的 highlight_shrink 设为false时，可在front-matter添加highlight_shrink: true来单独配置文章收缩代码框。
>

#### 代码换行

在默认情况下，Hexo在编译的时候不会实现代码自动换行，如果你不想代码换行的，那么可以考虑修改代码换行的属性。

```yml
# 进入_config.butterfly.yml
code_word_wrap: true
```

修改完之后，还需要根据你使用的渲染的进一步设置。

如果你是使用`highlight`渲染，需要找到你站点的`Hexo`配置文件`_config.yml`，将`line_number`改成`false`。

```yml
highlight:
  enable: true
  line_number: false # <- 改这里
  auto_detect: false
  tab_replace:
```

如果你是使用`prismjs`渲染，需要找到你站点的`Hexo`配置文件`_config.yml`，将`line_number`改成`false`。

```
prismjs:
  enable: false
  preprocess: true
  line_number: false # <- 改这里
  tab_replace: ''
```

在这里就没有修改了，因为我觉得还是需要不需要换行的好，有时候复制容易忽略代码换行了的问题，最后导致报错。

如果你设置了，那么代码框底部就不会有滑动条了。

![代码框底部滑动条](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E4%BB%A3%E7%A0%81%E6%A1%86%E5%BA%95%E9%83%A8%E6%BB%91%E5%8A%A8%E6%9D%A1.png)

#### 代码框高度

> 主题版本3.7.0以上支持

该属性可以设置代码框的高度，如果代码内容只会显示高度之内的，超出的部分会默认隐藏，并且显示展开按钮。

```yml
# 进入_config.butterfly.yml
highlight_height_limit: false # unit: px
```

**注意：**

1. 单位是`px`，直接添加数字，如 200，不需要我们手动添加单位了；
2. 虽然我们设置的是200px，但实际上代码框的限制高度是在我们设置的基础上再加30px，这样做的目的也是为了避免某段代码高度只超出`highlight_height_limit`设置的高度一点时，出现有展开按钮，但展开之后没内容的现象。
3. 不适用于隐藏后的代码块（ css 设置 display: none）

![hexo-theme-butterfly-docs-highlight-heigh-limit](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/hexo-theme-butterfly-docs-highlight-heigh-limit.gif)

### 社交图标

> 主题支持[font-awesome v6](https://fontawesome.com/icons?from=io)图标。

如何添加社交图标，只需要我们在主题配置文件（_config.butterfly.yml）中使用查找功能找到`social`，在主题配置文件中默认添加了两个社交图标，一个是github，一个是email，那么如何添加呢，只需要点击上面的链接，跳转到图标库中，找到我们需要的图标。

例如我想添加一个`Blog`，只需要搜索Blog，下面就会出现搜索出来的结果

![图标搜索1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%9B%BE%E6%A0%87%E6%90%9C%E7%B4%A21.png)

然后找到你喜欢的图标，点击进去

![图标搜索2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%9B%BE%E6%A0%87%E6%90%9C%E7%B4%A22.png)

获得属性之后，回到主题配置文件，找到`social`，在下面添加图标，其结构为：`图标名：url || 描述性文字 || color`。

```yml
social:
  fab fa-github: https://github.com/qichenxiaoni || Github || '#24292e'
  fas fa-envelope: mailto:xxxxxx@gmail.com || Email || '#4a7dbe'
  fa-solid fa-blog: https://qichenxiaoni.work || Blog || 'pink'
```

![图标配置展示](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%9B%BE%E6%A0%87%E9%85%8D%E7%BD%AE%E5%B1%95%E7%A4%BA.png)

> 后续会出如何更换图标库

### 头像

主题默认的头像是一个H，那怎么去修改呢，很简单，只需要到主题配置文件中找到`avatar`属性即可更换头像。

```yml
avatar:
  img: /img/avatar.png  # 支持本地图像，也支持网络链接
  effect: true # 头像会一直转圈，默认是false
```

### 顶部图

**注意：**由于这一部分有一些设置，我没有进行设置，并且该部分的一些设置会影响到后面的一些美化设置，因此，我在此部分简短地介绍我做的更改。

首先我在顶部图这一部分只做了两处修改，第一处是修改了主页的横幅，也就是一进博客的第一部分，第二部分就是页面顶部图片。

```yml
# 主页横幅
index_img: "./img/image1.png"
# 如果页面没有设置图片，则显示这个
default_top_img: "./img/image1.png" #(这个不知道为什么好像没生效)
```

> 需要注意的是：
>
> 1. 如果不要显示顶部图，可直接配置 `disable_top_img: true`;
> 2. 顶部图的获取顺序，如果都没有配置，则不显示顶部图;
> 3. 页面顶部图的获取顺序：各自配置的 top_img > 配置文件的 default_top_img;
> 4. 文章页顶部图的获取顺序：各自配置的 top_img > cover > 配置文件的 default_top_img
>

具体的配置还请前往博客教程文档查看。点击[此链接](https://butterfly.js.org/posts/4aa8abbe/#%E9%A0%82%E9%83%A8%E5%9C%96)跳转。

### 文章封面

文章的 markdown 文档上,在` Front-matter`添加` cover` ,并填上要显示的图片地址，如果不配置` cover`,可以设置显示默认的 `cover`，如果不想在首页显示 `cover`, 可以设置为 `false`。

```yml
# 进入主题配置文件
cover:
  # display the cover or not (是否顯示文章封面)
  index_enable: true   #主页是否显示文章封面图
  aside_enable: true   #侧栏是否显示文章封面图
  archives_enable: true   #归档页面是否显示文章封面图
  # the position of cover in home page (封面顯示的位置)
  # left/right/both 全左/全右/左右轮换
  position: both
  # When cover is not set, the default cover is displayed (當沒有設置cover時，默認的封面顯示)
  default_cover:
    - https://file.crazywong.com/gh/jerryc127/CDN@latest/cover/default_bg.png
    - https://file.crazywong.com/gh/jerryc127/CDN@latest/cover/default_bg2.png
    - https://file.crazywong.com/gh/jerryc127/CDN@latest/cover/default_bg3.png
```

### 主页文章节选（自动节选和文章页description）

因为主题UI的关系，主页文章节选仅仅支持自动节选以及文章页description，自动节选就是默认从你的文章中摘选你设置`length`个字展示出来，文章页`description`就是你自己在`froot-matter`中添加一个`desciption`，你自己填入值。

```yml
# 修改配置文件
# Display the article introduction on homepage
# 1: description  # 只显示description；
# 2: both (if the description exists, it will show description, or show the auto_excerpt)  #  优先选择description，如果没有配置description，则显示自动节选的内容
# 3: auto_excerpt (default)   # 只显示自动节选
# false: do not show the article introduction  # 不显示文章内容
index_post_content:
  method: 2
  length: 500 # if you set method to 2 or 3, the length need to config （如果你选择了2/3，那么长度`length`就需要配置）
```

> `description`在`front-matter`里添加。

### 内容复制相关配置

该选项可以配置网站文章是否允许被复制，复制时带不带版权信息已经复制多少就在复制内容之后添加版权信息。

```yml
# 进入主题配置文件
# copy settings
# copyright: Add the copyright information after copied content (複製的內容後面加上版權信息)
copy:
  enable: true
  copyright: 
    enable: true
    limit_count: 50
```

| 配置        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| enable      | 是否开启网站复制权限                                         |
| copyright   | 复制内容后面加上版权信息                                     |
| enable      | 是否开启复制版权信息添加                                     |
| limit_count | 字数限制，当复制字数超过此限制时，将在复制内容后面加上版权信息 |

eg：

![文章复制权限](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E6%96%87%E7%AB%A0%E5%A4%8D%E5%88%B6%E6%9D%83%E9%99%90.png)

### 文章页面配置

#### 文章版权

顾名思义，为你的博客文章展示文章的版权以及许可协议，具体操作进去主题配置文件，找到`post_copyright`，修改相关配置。

```yml
post_copyright:
  enable: true
  decode: false
  author_href:
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/
```

**注意：**由于Hexo 4.1开始，默认对网址进行解码，以至于如果是中文网址，会被解码，可设置`decode: true`来显示中文网址。

> true

![开启解码](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%BC%80%E5%90%AF%E8%A7%A3%E7%A0%81.png)

> false

![关闭解码](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%85%B3%E9%97%AD%E8%A7%A3%E7%A0%81.png)

当然了，如果文章是转载的，并非原创，不需要显示版权的，可以在文章`Front-matter`单独设置，也支持对文章单独设置版权信息，也是在文章的`Front-matter`单独设置。

```markdown
# 转载
copyright: false
# 单独设置版权
copyright_author: xxxx
copyright_author_href: https://xxxxxx.com
copyright_url: https://xxxxxx.com
copyright_info: 此文章版权归xxxxx所有，如有转载，请注明来自原作者
```

#### TOC

在文章页面，会有目录，用来显示TOC，那么如何设置呢？只需要我们进入主题配置文件，找到`toc`，然后修改下面的配置即可。

```yml
# toc (目錄)
toc:
# 文章页是否显示TOC
  post: true
  # 普通页面是否显示toc
  page: false
  # 是否显示章节数
  number: true
  # 是否展开toc
  expand: true
  # 简介模式 （侧边栏只显示TOC，只对文章页有效）
  style_simple: false # for post
  # 实现显示滚动进度百分比
  scroll_percent: true
```

##### 为特定文章配置

如果你的某些文章他不需要toc，或者需要toc其他的设置的时候，只需要在你文章的头部，也就是`Front-matter`里面添加`toc_number`和`toc`，并配置`true`或者`false`即可，也不用担心在文章中设置是否能生效，因为文章中的`Front-matter`的优先级是要高于主题配置文件的。

#### 相关文章

相关文章就是在你的文章尾部根据文章的`tag`的比重来推荐的，那么怎么设置显示推荐文章的数量呢，需要我们进入主题配置文件中，找到`related_post`，修改其配置即可。

```yml
# Related Articles
related_post:
  enable: true
  limit: 6 # 显示推荐文章数目
  date_type: created # or created or updated 文章日期顯示創建日或者更新日
```

![相关推荐](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E7%9B%B8%E5%85%B3%E6%8E%A8%E8%8D%90.png)

> 当文章封面设置为 false 时，或者没有获取到封面配置，相关文章背景将会显示主题色。

#### 文章过期提示

因为有一部分的博客内容会随着时间的变化而产生改变，也就是说或许在之前是可以使用的，但是可能随着时间变化，某些东西消失了，或者是更新了，原本的内容就不再适用了，因此可以设置一个这个过期提示告诉他人，这个内容是多久多久前写的，可能已经失效了或是不适用了。

那么怎么来设置呢，只需要进入主题配置文件中，找到`noticeOutdate`，修改其下面的配置即可。

```yml
# Displays outdated notice for a post (文章過期提醒)
noticeOutdate:
  enable: true
  style: flat # style: simple/flat
  limit_day: 183 # When will it be shown
  position: top # position: top/bottom
  message_prev: It has been
  message_next: days since the last update, the content of the article may be outdated.
```

#### 最后

原本还有一些文章页面配置的，但是由于我没使用那些，因此没有进行说明，例如文章编辑按钮、文章分页按钮以及文章打赏，如果有需求的，可以点击[此链接](https://butterfly.js.org/posts/4aa8abbe/#%E6%96%87%E7%AB%A0%E7%89%88%E6%AC%8A)跳转过去设置。

### Footer设置

#### 博客年份设置

`since`是一个来展示你站点起始时间的选项。它位于页面的最底部，如果需要设置，那么进入主题配置文件，找到`footer`，进行修改。

```yml
footer:
  owner:
    enable: true
    since: 2023
```

#### 页脚自定义文本

`custom_text`是一个给你用来在页脚自定义文本的选项。通常你可以在这里写声明文本等。支持 HTML，如果需要设置，那么进入主题配置文件，找到`footer`，进行修改。

```yml
# Footer Settings
# --------------------------------------
footer:
  owner:
    enable: true
    since: 2023
  custom_text: 欢迎来到小陈的博客空间
  copyright: true # Copyright of theme and framework
```

![footer](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/footer.png)

### 侧边栏设置

#### 侧边排版

侧边排版的设置很多，也很详细，他可以让我们自行决定哪个项目需要显示，怎么显示，位置在哪里，也可以设置整个侧边栏不显示。

进入主题配置文件，找到`aside`，修改下面的配置即可。

```yml
aside:
# 是否开启侧边栏
  enable: true
  hide: false
  # 是否显示按钮
  button: true
  mobile: true # display on mobile
  position: right # left or right
  display:
    archive: true
    tag: true
    category: true
  card_author:
    enable: true
    description: 
    button:
      enable: true
      icon: fab fa-github
      text: Follow Me
      link: https://github.com/xxxxxx
  card_announcement:
    enable: true
    content: This is my Blog
  card_recent_post:
    enable: true
    limit: 5 # if set 0 will show all
    sort: date # date or updated
    sort_order: # Don't modify the setting unless you know how it works
  card_categories:
    enable: true
    limit: 8 # if set 0 will show all
    expand: none # none/true/false
    sort_order: # Don't modify the setting unless you know how it works
  card_tags:
    enable: true
    limit: 40 # if set 0 will show all
    color: true  # 是否标签有颜色
    orderby: random # Order of tags, random/name/length
    order: 1 # Sort of order. 1, asc for ascending; -1, desc for descending
    sort_order: # Don't modify the setting unless you know how it works
  card_archives:
    enable: true
    type: monthly # yearly or monthly
    format: MMMM YYYY # eg: YYYY年MM月
    order: -1 # Sort of order. 1, asc for ascending; -1, desc for descending
    limit: 8 # if set 0 will show all
    sort_order: # Don't modify the setting unless you know how it works
  card_webinfo:
    enable: true
    post_count: true
    last_push_date: true
    sort_order: # Don't modify the setting unless you know how it works
```

由于侧边栏排版的设置多样性强，我也没有完全试完，如果有兴趣的可以自行摸索一下，这里就不多做介绍了。

#### 访问人数 busuanzi (UV 和 PV)

这个我自认为没有多大的用处，首先个人博客大概率是不会有很多人看的，并且busuanzi开启之后，数据是不对的，必须要格式化清空一遍，但是没找到格式化清空的有效方法，因此没设置，但如果有需求的朋友或者是知道怎么格式化清空的朋友也可以试试。

进入主题配置文件，找到`busuanzi`，修改下面的配置。

```yml
busuanzi:
  site_uv: true
  site_pv: true
  page_pv: true
```

同时如果你需要修改busuanzi的CDN链接，可以到主题配置文件中搜索CDN，进行修改。

```yml
CDN:
  option:
    busuanzi: xxxxxxxxx
```

#### 运行时间

这个设置就是显示该个人博客运行了多久了，可设置也可不设置，全凭个人意愿，如果需要设置，进入主题配置文件，搜索`runtimeshow`，将`enable`设置为`true`和` publish_date:`设置为具体的时间（可以是月/日/年 时间，也可以是年/月/日 时间）。

```
runtimeshow:
  enable: true
  publish_date: 2023/4/15 00:00:00
  ##网页开通时间
  #格式: 月/日/年 时间
  #也可以写成 年/月/日 时间
```

![网站运行时间](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E7%BD%91%E7%AB%99%E8%BF%90%E8%A1%8C%E6%97%B6%E9%97%B4.png)

#### 最后

侧边栏设置还有最新评论以及自定义侧边栏，由于我没有设置了，因此有需要的朋友可以自行前往主题官方文档进行查看修改，点击[此链接](https://butterfly.js.org/posts/4aa8abbe/#%E6%9C%80%E6%96%B0%E8%A9%95%E8%AB%96)进行跳转。

### 功能按钮

#### 简繁转换按钮

简体繁体互换，右下角会有简繁转换按钮，修改主题配置文件，找到`translate`进行修改。

```yml
# Conversion between Traditional and Simplified Chinese (簡繁轉換)
translate:
  enable: true
  # The text of a button
  default: 繁
  # the language of website (1 - Traditional Chinese/ 2 - Simplified Chinese）
  defaultEncoding: 2
  # Time delay
  translateDelay: 0
  # The text of the button when the language is Simplified Chinese
  msgToTraditionalChinese: '繁'
  # The text of the button when the language is Traditional Chinese
  msgToSimplifiedChinese: '簡'
```

> 这个简繁转换还是有时候会存在部分字体转换不完全的现象

#### 阅读模式

阅读模式下会去掉除文章外的内容，避免干扰阅读，只会出现在文章页面，右下角会有阅读模式按钮，修改主题配置文件，找到`readmode`改成true即可。

#### 夜间模式

```yml
# dark mode
darkmode:
  enable: true
  # Toggle Button to switch dark/light mode
  button: true
  # Switch dark/light mode automatically (自動切換 dark mode和 light mode)
  # autoChangeMode: 1  Following System Settings, if the system doesn't support dark mode, it will switch dark mode between 6 pm to 6 am
  # autoChangeMode: 2  Switch dark mode between 6 pm to 6 am
  # autoChangeMode: false
  autoChangeMode: false
  # Set the light mode time. The value is between 0 and 24. If not set, the default value is 6 and 18
  start: # 8
  end: # 22
```

| 参数           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| button         | 是否在右下角显示日夜模式切换按钮                             |
| autoChangeMode | 自动切换的模式<br />autoChangeMode: 1 跟随系统而变化，不支持的浏览器/系统将按照时间 start 到 end 之间切换为 light mode<br/>autoChangeMode: 2 只按照时间 start 到 end 之间切换为 light mode ,其余时间为 dark mode<br/>autoChangeMode: false 取消自动切换<br/> |
| start          | light mode 的开始时间                                        |
| end            | light mode 的结束时间                                        |

#### 滚动状态百分比

```yml
# show scroll percent in scroll-to-top button
rightside_scroll_percent: true
```

![滚动状态百分比](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E6%BB%9A%E5%8A%A8%E7%8A%B6%E6%80%81%E7%99%BE%E5%88%86%E6%AF%94.gif)

#### 按钮排序

```yml
# Don't modify the following settings unless you know how they work (非必要请不要修改 )
# Choose: readmode,translate,darkmode,hideAside,toc,chat,comment
# Don't repeat 不要重复
rightside_item_order:
  enable: false
  hide: # readmode,translate,darkmode,hideAside
  show: # toc,chat,comment
```

## 结语

至此，我们就完成了主题的深入配置一，当然了，主题官方文档还准备了一些标签插件，但是我由于没有使用，因此有需要的朋友点击[链接](https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89)自行跳转观看。接下来进入深入配置二。



<本文完>



> 本篇文章参考[官方文档](https://butterfly.js.org/posts/4aa8abbe/)

