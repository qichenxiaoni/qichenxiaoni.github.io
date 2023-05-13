# 创建Hexo博客之前期准备


## 前言

[Hexo](https://hexo.io/zh-cn/index.html)是一款基于Node.js的静态博客生成器。他可以帮助用户快速、轻松地创建并部署自己的博客网站。

Hexo的主要特征包括以下几点：

1. 快速：Hexo采用了缓存机制和异步渲染技术，生成速度非常快；
2. 简单易用：Hexo的配置非常简单，它支持大量的[主题](https://hexo.io/themes/)和[插件](https://hexo.io/plugins/)，使得用户可以快速打造自己的个性化博客；
3. Markdown支持： Hexo支持使用Markdown语法来编写文章，并且可以直接在命令行界面预览效果；
4. 多平台支持：Hexo可以发布到多种平台，例如：Github Pages、HeroKu以及Netlity等等；
5. 插件丰富：Hexo有大量的插件可以供选择，如SEO优化、社交分享等，可以很大程度上满足用户的各种需求；

总而言之，Hexo是一款非常优秀的博客生成器，它能够让用户快速地创建自己的博客网站，并提供了十分丰富的主题和插件来满足用户的需求。

## 安装准备

在安装Hexo之前，我们必须保证自己的设备中存在以下软件：git（版本控制器）、node（运行环境）以及可以使用 npm 或者是 cnpm （包管理工具）；

如果已经有则可以进行下一步操作，如果设备中不存在或缺少可以点击下方链接进行跳转。

- git：请点击[此链接](https://git-scm.com/)；

- node：请点击[此链接](https://nodejs.org/zh-cn)

- npm或cnpm：npm是当你安装好node之后就自动拥有的，我们需要的是对npm进行淘宝镜像的配置；cnpm是一个完整的`npmjs.org`镜像，由于npm的服务器是国外的，需要进行配置，因此cnpm便应运而生，用法都是差不多的，只是需要先下载后配置再使用。

  ```shell
  # 1.临时使用
  npm --registry https://registry.npm.taobao.org install express
  
  # 2.持久使用
  
  npm config set registry https://registry.npm.taobao.org
  
  # 2.1. 配置后可通过下面方式来验证是否成功
  npm config get registry
  
  # 3. 通过cnpm使用
  
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  
  # 3.1. 使用
  cnpm install express 
  ```

<本文完>

