# 创建Hexo博客之Hexo主题配置2


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

### 搜索

顾名思义就是在个人博客中添加一个搜索功能，作者给出了三种搜索方式，第一种是`Algolia`，第二种是本地搜索，第三种是`DocSearch`，在这里我们使用第二种方法，也就是本地搜索。

如果使用本地搜索的方法，首先第一需要安装[hexo-generator-searchdb](https://github.com/next-theme/hexo-generator-searchdb)或者[hexo-generator-search](https://github.com/PaicHyperionDev/hexo-generator-search)这两个中的其中一个，点击链接，根据文档来进行相关的配置。（本人使用的是第二个链接）

```zsh
# 安装依赖
npm install hexo-generator-search --save
```

安装好依赖之后，回到主题配置文件，使用查找功能找到`local_search`，修改相关配置。

```yml
# Local search
local_search:
  enable: true
  # Preload the search data when the page loads.
  preload: false
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  CDN:
```

| 参数              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| enable            | 是否开启本地搜索                                             |
| preload           | 预加载，开启后，进入网页后会自动加载搜索文件。关闭时，只有点击搜索按钮后，才会加载搜索文件 |
| top_n_per_article | 匹配的文章结果，默认显示最开始的1段结果                      |
| unescape          | 将html字符串解码为可读字符串                                 |
| CDN               | 搜索文件的 CDN 地址（默认使用的本地链接）                    |

> 记得运行 hexo clean

### 评论

关于评论设置，作者也给出了多种方法，在这里我选择的是`livere`，也就是来必力。

1. 首先注册一个[来必力](https://livere.com/)账号，如果没有的话；
2. 登录来必力之后，进入管理页面，可以修改一下设置里面的'网站的URL'，将其设置为自己的域名；
3. 来到代码管理页面，复制里面的`data_uid`，记住这一个`UID`在后面很重要的；
4. 复制好uid之后回到主题配置文件里面，找到`livere`，将复制好的uid复制进去即可。

![来必力UID](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E6%9D%A5%E5%BF%85%E5%8A%9BUID.png)

![评论设置](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E8%AF%84%E8%AE%BA%E8%AE%BE%E7%BD%AE.png)

到此，评论系统也就配置完成了。

### 美化与特效

#### 网站背景

网站的默认背景显示为白色，可以为其设置为图片或其他的颜色。

进入主题配置文件，找到`backgorund`，修改配置即可。

```yml
# Website Background (設置網站背景)
# can set it to color or image (可設置圖片 或者 顔色)
# The formal of image: url(http://xxxxxx.com/xxx.jpg)
background: url(/img/image1.png)
```

> 留意: 如果你的网站根目录不是'/',使用本地图片时，需加上你的根目录。
> 例如：网站是 https://yoursite.com/blog,引用一张img/xx.png图片，则设置background为 `url(/blog/img/xx.png)

#### footer背景

这个设置如果你需要在后期使用css样式来修改的话，这里千万不要设置为`true`，因为如果你css里面设置它为透明色，他不会生效的。

```yml
# footer是否显示图片背景(与top_img一致)
footer_bg: false
```

![footer设置](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/footer%E8%AE%BE%E7%BD%AE.png)

### 页面美化

会改变ol、ul、h1-h5的样式，field配置生效的区域：post 只在文章页生效、site 在全站生效
进入主题配置文件，修改相关配置。

```yml
# 美化页面显示
beautify:
  enable: true
  field: site # site/post
  title-prefix-icon: '\f0c1'
  title-prefix-icon-color: "#F47466"
```

> 需要注意的是，`title-prefix-icon`的值是图标的`Unicode`。

![图标](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%9B%BE%E6%A0%87.png)

### 网站副标题

可设置主页中显示的网站副标题或者喜欢的座右铭。

修改主题配置文件

```yml
# the subtitle on homepage (主頁subtitle)
subtitle:
  enable: true
  # Typewriter Effect (打字效果)
  effect: true
  # Customize typed.js (配置typed.js)
  # https://github.com/mattboldt/typed.js/#customization
  typed_option: 
  # source 調用第三方服務
  # source: false 關閉調用
  # source: 1  調用一言網的一句話（簡體） https://hitokoto.cn/
  # source: 2  調用一句網（簡體） https://yijuzhan.com/
  # source: 3  調用今日詩詞（簡體） https://www.jinrishici.com/
  # subtitle 會先顯示 source , 再顯示 sub 的內容
  source: 2
  # 如果關閉打字效果，subtitle 只會顯示 sub 的第一行文字
  sub:
    - 今日事&#44;今日毕
    - Never put off till tomorrow what you can do today
```

![hexo-theme-butterfly-doc-index-subtitle](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/hexo-theme-butterfly-doc-index-subtitle.gif)

### 字数统计

要为Butterfly配上字数统计特性, 你需要如下几个步骤:

1. 打开 hexo 工作目录

2. npm install hexo-wordcount --save

3. 修改 主题配置文件:

```
wordcount:
  enable: true
  post_wordcount: true
  min2read: true
  total_wordcount: true
```

![字数统计](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%AD%97%E6%95%B0%E7%BB%9F%E8%AE%A1.png)

### 图片大图展示

进入主题配置文件，搜索`fancybox`，将值改为`true`，即可。

![fancybox](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/fancybox.gif)

当然还有一种方法，那就是进去主题配置文件，搜索`medium_zoom`的值改为`true`即可。

![medium_zoom](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/medium_zoom.gif)

> 只能开启一个

### Pjax

当用户点击链接，通过ajax更新页面需要变化的部分，然后使用HTML5的pushState修改浏览器的URL地址。这样可以不用重复加载相同的资源（css/js）， 从而提升网页的加载速度。

```yml
# Pjax
# It may contain bugs and unstable, give feedback when you find the bugs.
# https://github.com/MoOx/pjax
pjax:
  enable: true
  exclude:
    # - xxxx
    # - xxxx
```

### Pangu

如果你每次看到网页上的中文字和英文、数字、符号挤在一块，就会坐立难安，忍不住想在它们之间加个空格。这个外挂正是你在网路世界走跳所需要的东西，它会自动替你在网页中所有的中文字和半形的英文、数字、符号之间插入空白。

```yml
# https://github.com/vinta/pangu.js
# Insert a space between Chinese character and English character (中英文之間添加空格)
pangu:
  enable: true
  field: site # site/post
```

> field只支持两个参数，post(只在文章页生效)和site(全站生效)

### 添加全局吸底Aplayer教程

进入主题配置文件。

#### 开启主题的aplayerInject

```yml
# Inject the css and script (aplayer/meting)
aplayerInject:
  enable: true
  per_page: true
```

#### 插入Aplayer html

```yml
inject:
  head:
    - <link rel="stylesheet" href="/css/style.css">
  bottom:
    - <div class="aplayer no-destroy" data-id="60198" data-server="netease" data-type="playlist" data-fixed="true" data-autoplay="true"> </div>
```

![音乐播放器](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E9%9F%B3%E4%B9%90%E6%92%AD%E6%94%BE%E5%99%A8.png)

### CSS样式

虽然该主题的自定义能力蛮不错，但是总会有一些地方不尽如人意，又因为他也支持CSS样式表来修改，所以我们就来使用CSS样式表来让博客更加美观。

首先在博客根目录下的`source`文件夹中创建一个`css`文件夹，在其中创建一个css样式表文件，名字随意，创建好之后进行添加css样式即可，这里我给出我的css样式表的代码来作为参考。

```css
#footer {
    background: transparent;
}

/* 鼠标样式 */
body {
    cursor: url(https://cdn.jsdelivr.net/gh/constown/HexoCustomFile/public/cursors/default.cur),
      default;
  }
  a,
  img {
    cursor: url(https://cdn.jsdelivr.net/gh/constown/HexoCustomFile/public/cursors/pointer.cur),
      default;
  }

/* 滚动条样式 */
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
  }
  
  ::-webkit-scrollbar-track {
    background-color: rgba(73, 177, 245, 0.2);
    border-radius: 2em;
  }
  
  ::-webkit-scrollbar-thumb {
    background-color: #49b1f5;
    background-image: -webkit-linear-gradient(
      45deg,
      rgba(255, 255, 255, 0.4) 25%,
      transparent 25%,
      transparent 50%,
      rgba(255, 255, 255, 0.4) 50%,
      rgba(255, 255, 255, 0.4) 75%,
      transparent 75%,
      transparent
    );
    border-radius: 2em;
  }
  
  ::-webkit-scrollbar-corner {
    background-color: transparent;
  }
  
  ::-moz-selection {
    color: #fff;
    background-color: #49b1f5;
  }
```

编写好之后，怎么引用这个样式表呢，只需要在主题配置文件中找到`inject`，修改`head`，将css样式表引用进去即可。

```yml
inject:
  head:
    - <link rel="stylesheet" href="/css/style.css">
```



## 结语

至此，butterfly主题的hexo个人静态博客就到此结束了，如果还有什么需求，可以先去主题官方文档中查看，之后再去网上搜索。



<本文完>



> 本篇文章参考[官方文档](https://butterfly.js.org/posts/4aa8abbe/)

