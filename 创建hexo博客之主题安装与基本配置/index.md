# 创建Hexo博客之主题安装与基本配置


## 前言

[Hexo](https://hexo.io/zh-cn/index.html)是一款基于Node.js的静态博客生成器。他可以帮助用户快速、轻松地创建并部署自己的博客网站。

Hexo的主要特征包括以下几点：

1. 快速：Hexo采用了缓存机制和异步渲染技术，生成速度非常快；
2. 简单易用：Hexo的配置非常简单，它支持大量的[主题](https://hexo.io/themes/)和[插件](https://hexo.io/plugins/)，使得用户可以快速打造自己的个性化博客；
3. Markdown支持： Hexo支持使用Markdown语法来编写文章，并且可以直接在命令行界面预览效果；
4. 多平台支持：Hexo可以发布到多种平台，例如：Github Pages、HeroKu以及Netlity等等；
5. 插件丰富：Hexo有大量的插件可以供选择，如SEO优化、社交分享等，可以很大程度上满足用户的各种需求；

总而言之，Hexo是一款非常优秀的博客生成器，它能够让用户快速地创建自己的博客网站，并提供了十分丰富的主题和插件来满足用户的需求。

## 安装主题

本项目中安装的Hexo主题是butterfly，首先我们去[hexo官方主题页面](https://hexo.io/themes/)，搜索我们想要的主题并点击，或者如果主题在github上有仓库，那么我们可以github上搜索`hexo-theme`，找到心仪的主题。

butterfly主题给出了三种不同的安装，分别是从github仓库中克隆、从gitee仓库中克隆以及使用npm方法进行安装。

在这里我使用的是npm安装方法，需要注意的是，使用npm安装必须要求在前面安装时Hexo的安装版本必须在5.0.0以上，同时使用npm安装，不会在根目录下的themes文件夹中生成主题文件夹，主题会被放在`node_modules`中。

```shell
npm install hexo-theme-butterfly
```

> 升级的方法是在根目录下执行`npm update hexo-theme-butterfly`，同时，建议去github中的Releases或者主题文档中的文档七查看最新版的更新内容，里面有标注`_config`文件的变更内容，如果有标注，则根据实际情况进行更新配置。

当我们安装好主题之后，接下来就是需要应用主题，直接进入根目录下的`_config.yml`文件中，找到`theme`，将默认的landscape更改为butterfly即可。

这个时候我们就已经完成了主题的安装和应用，但是由于这个主题需要pug和stylus的渲染器，不确定我们有没有，所以执行安装这两个插件的命令

``` shell
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

### 升级建议

为了减少主题升级之后带来的不方便，因此我们可以在根目录下创建一个`_config.butterfly.yml`文件，并且将主题文件夹中的`_config.yml`文件里面的内容复制一份到刚刚创建好的`_config.butterfly.yml`文件内（**注意：是到`node_modules`文件夹的主题文件夹中，复制里面的`_config.yml`文件内容，而不是外面的`_config.yml`文件内容，粘贴到外面的`_config.butterfly.yml`**）

> 需要注意的是，不能将主题文件夹中的`_config.yml`文件删除，然后以后更改内容也只需要在`_config.butterfly.yml`文件中修改配置即可。

## 基本配置

### 创建基本页面

#### 创建标签页

进入博客根目录下，打开终端，输入`hexo new page tags`命令，找到`source/tags/index.md`，修改里面的内容，**切记一定要在Front-matter里面添加`type: "tags"`**

```yml
---
title: 小陈的标签页  # 这个可以随意修改名字
date: 2023-04-14 20:54:26
type: "tage"  # 这个要添加
---
```

#### 创建分类页

进入博客根目录下，打开终端，输入`hexo new page categories`命令，找到`source/categories/index.md`，修改里面的内容，**切记一定要在Front-matter里面添加`type: "categories"`**。

```yml
---
title: 我们终会遇见美好  # 这个可以随意修改名字
date: 2023-04-14 20:55:27
type: "categories"    # 这个要添加
---
```

#### 创建友情链接

进入博客根目录下，打开终端，输入`hexo new page link`命令，找到`source/link/index.md`，修改里面的内容，**切记一定要在Front-matter里面添加`type: "link"`**。

```yml
---
title: 小陈的朋友们    # 这个可以随意修改名字
date: 2023-04-14 20:55:56
type: "link"    # 这个要添加
---
```

##### 添加友情链接

有了友情链接的页面，就需要添加一些友链，那么怎么去添加呢，一共有两种方法，一种是本地生成的。这种方法就需要你在根目录下的`source/_data`文件夹中创建一个`link.yml`文件，（如果没有`_data`文件夹，请自行创建一个，切记data前面是下划线'_'，不是'-'），可以先复制官方文档中的内容，后期再进行修改或添加。

```yml
- class_name: 友情链接
  class_desc: 那些人，那些事
  link_list:
    - name: Hexo
      link: https://hexo.io/zh-tw/
      avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg
      descr: 快速、简单且强大的网志框架

- class_name: 网站
  class_desc: 值得推荐的网站
  link_list:
    - name: Youtube
      link: https://www.youtube.com/
      avatar: https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.png
      descr: 视频网站
    - name: Weibo
      link: https://www.weibo.com/
      avatar: https://i.loli.net/2020/05/14/TLJBum386vcnI1P.png
      descr: 中国最大社交分享平台
    - name: Twitter
      link: https://twitter.com/
      avatar: https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.png
      descr: 社交分享平台
```

第二种方法是远程拉取，该方法是从4.0.0以后，就支持远程拉取了，需要注意的是，如果远程拉取加载成功之后，本地生产的就失效了，并且远程拉取支持的格式仅仅只有`json`。

如果需要远程拉取，则需要在 source/link/index.md 这个文件的 front-matter 添加远程链接，

```
flink_url: xxxxx # json文件的位置
```

下面是官方文档中关于远程拉取的json文件模板

```json
[
  {
    "class_name": "友情链接",
    "class_desc": "那些人，那些事",
    "link_list": [
      {
        "name": "Hexo",
        "link": "https://hexo.io/zh-tw/",
        "avatar": "https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg",
        "descr": "快速、简单且强大的网志框架"
      }
    ]
  },
  {
    "class_name": "网站",
    "class_desc": "值得推荐的网站",
    "link_list": [
      {
        "name": "Youtube",
        "link": "https://www.youtube.com/",
        "avatar": "https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.png",
        "descr": "视频网站"
      },
      {
        "name": "Weibo",
        "link": "https://www.weibo.com/",
        "avatar": "https://i.loli.net/2020/05/14/TLJBum386vcnI1P.png",
        "descr": "中国最大社交分享平台"
      },
      {
        "name": "Twitter",
        "link": "https://twitter.com/",
        "avatar": "https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.png",
        "descr": "社交分享平台"
      }
    ]
  }
]
```

#### 创建404页面

主题中内置了一个简单的404界面，我们可以在设置中搜索开启

> 需要额外注意的是，在本地预览时，如果我们访问出错了的网站是不会自动跳转到404页面的，如果想在本地预览时查看404页面的效果，需要访问`http://localhost:4000/404.html`。

```
# A simple 404 page
error_404:
  enable: true
  subtitle: '不好意思，页面走丢啦'  # 这个可以自由编辑
  background: https://i.loli.net/2020/05/19/aKOcLiyPl2JQdFD.png
```

![404页面](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/404%E9%A1%B5%E9%9D%A2.png)

#### 最后

官方文档中还提到了添加图库以及子页面的方法，但是由于我暂时用不上，因此在这里没有配置这一项，如果有需要的，可以访问[官方文档](https://butterfly.js.org/posts/dc584b87/#404%E9%A0%81%E9%9D%A2)，根据文档中的教程一步一步配置。



## 总结

至此，我们就已经完成hexo主题的下载更换以及一些基本配置，下面我们就针对主题进行更深入的修改配置。



<本文完>

> 本篇文章参考[官方文档](https://butterfly.js.org/posts/dc584b87/)
