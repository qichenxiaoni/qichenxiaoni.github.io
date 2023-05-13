# 创建Hexo博客之Hexo安装


## 前言

[Hexo](https://hexo.io/zh-cn/index.html)是一款基于Node.js的静态博客生成器。他可以帮助用户快速、轻松地创建并部署自己的博客网站。

Hexo的主要特征包括以下几点：

1. 快速：Hexo采用了缓存机制和异步渲染技术，生成速度非常快；
2. 简单易用：Hexo的配置非常简单，它支持大量的[主题](https://hexo.io/themes/)和[插件](https://hexo.io/plugins/)，使得用户可以快速打造自己的个性化博客；
3. Markdown支持： Hexo支持使用Markdown语法来编写文章，并且可以直接在命令行界面预览效果；
4. 多平台支持：Hexo可以发布到多种平台，例如：Github Pages、HeroKu以及Netlity等等；
5. 插件丰富：Hexo有大量的插件可以供选择，如SEO优化、社交分享等，可以很大程度上满足用户的各种需求；

总而言之，Hexo是一款非常优秀的博客生成器，它能够让用户快速地创建自己的博客网站，并提供了十分丰富的主题和插件来满足用户的需求。

## 安装

首先在最开始，需要确保我们电脑中有git工具和node.js，以及已经配置好了npm的淘宝镜像或者是cnpm，如果没有配置好，可以参考我上一篇博客，[创建Hexo博客之前期准备](https://www.chenxiaoni.work/2023/04/16/%E5%88%9B%E5%BB%BAHexo%E5%8D%9A%E5%AE%A2%E4%B9%8B%E5%89%8D%E6%9C%9F%E5%87%86%E5%A4%87/)，如果已经配置好一切，那么请继续。

### 安装Hexo

创建一个文件夹，在任何地方都可以，我们可已经其命名为Blog，然后在代码编辑器里面将这个文件夹打开（这里我使用的是VSCode），并打开其终端。

在终端中输入`npm install hexo -g`进行全局安装

```
# 安装Hexo
npm install hexo -g
# 查看是否安装成功
hexo version
```

![检测hexo是否安装成功](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E6%A3%80%E6%B5%8Bhexo%E6%98%AF%E5%90%A6%E5%AE%89%E8%A3%85%E6%88%90%E5%8A%9F.png)

在我们安装完成之后，接下来就可以进行初始化项目的操作了。

```
# 进入Blog文件夹中，输入
hexo init
```

在初始化的之后，可能会出现Blog文件夹中没有`node_modules`文件夹，当出现这个情况的时候，我们可以执行`npm install`的命令安装所需要的依赖文件。

```
npm install
```

![安装所需要的依赖](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%AE%89%E8%A3%85%E6%89%80%E9%9C%80%E8%A6%81%E7%9A%84%E4%BE%9D%E8%B5%96.png)

当我们执行完上面的所有步骤之后，我们就可以运行指令查看初步的hexo个人博客是否搭建成功

```
# 清除缓存
hexo clean
# 重新生成文件
hexo g
# 运行
hexo s
```

![hexo运行](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/hexo%E8%BF%90%E8%A1%8C.png)

如果能顺利执行以上的命令并且出现`http://localhost:4000`的时候就证明已经运行成功了。

![查看是否成功运行](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E6%9F%A5%E7%9C%8B%E6%98%AF%E5%90%A6%E6%88%90%E5%8A%9F%E8%BF%90%E8%A1%8C.png)

> 如果想要退出本地发布，可以在终端中输入Ctrl+C来停止。

至此，Hexo的安装就告一段落了，接下来我们对博客的配置文件进行简单的修改吧。

### 简单配置

进入Blog文件夹中找到`_config.yml`文件，可以根据我的来修改你以下的配置。

```
title: '小陈的博客'  ## 博客名字
subtitle: '一个想摆烂的代码人' ## 博客的副标题
description: '欢迎来到摆烂的代码世界' ## 头像下面的个人短介
keywords: Blog  ##博客的关键字
author: Chen  ## 作者名字
language: zh-CN  ## 显示语言类型
timezone: ''   ## 时区

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: http://qichenni.github.io
```

![博客初步设置](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%8D%9A%E5%AE%A2%E5%88%9D%E6%AD%A5%E8%AE%BE%E7%BD%AE.png)

**注意：**修改完之后重新运行推荐执行`hexo clean`、`hexo g`以及`hexo s`，因为有时候可能会在你修改之后运行不生效，需要清除缓存之后重新生成之后再发布出去。不过我们修改根目录下的`package.json`文件，找到`"server"`，修改后面的值，在原本的`hexo server`前面加上`hexo clean 和 hexo generate`，在它们三个之间一定要加上`&&`来表示并。

### 上传GitHub

到目前为止，我们所做的个人博客还仅仅只能是本地查看，不能让其他人看到，那怎么能出去装呢，所以我们这时候可以使用 `Github Pages`这项功能来实现，并且我们也可以将源代码上传到github上，这样就可以预防当我们换设备之后也可以很快的获取原来的文件，而不用重新再弄一次。

#### 创建仓库

新建一个名为你的用户名.github.io 的仓库，如果你的 github 用户名是 test，那么你就新建 test.github.io 的仓库（必须是你的用户名，其它名称无效），将来你的网站访问地址就是 http://test.github.io 了。

![创建github.io仓库](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%88%9B%E5%BB%BAgithub.io%E4%BB%93%E5%BA%93.png)

然后再创建一个存储博客源代码的仓库，这个仓库的命名没有任何要求，甚至仓库的状态是公开还是私密都没有什么影响。

![创建源文件仓库](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E5%88%9B%E5%BB%BA%E6%BA%90%E6%96%87%E4%BB%B6%E4%BB%93%E5%BA%93.png)

因为我们没有勾选自动生成README.md文件，所以仓库一创建，就会告诉你不同情况如何上传文件。

![仓库上传文件步骤](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E4%BB%93%E5%BA%93%E4%B8%8A%E4%BC%A0%E6%96%87%E4%BB%B6%E6%AD%A5%E9%AA%A4.png)

#### 配置秘钥以及git

##### 配置秘钥

进入终端，创建SSH key，（我是linux系统下，不同系统在这一步有不同设置）

```
# 进入.ssh文件夹
cd ~/.ssh
# 生成秘钥文件（邮箱地址可写可不写）
ssh-keygen -t rsa -C "你的邮箱地址"
# 查看生成的秘钥文件
cat ~/.ssh/id_rsa.pub
# 复制秘钥
```

复制好生成的秘钥之后，回到github上，进入settings里面，点击左边栏中的`SSH and GPG keys`，进去之后，点击右上角的`New SSH key`

![配置ssh1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E9%85%8D%E7%BD%AEssh1.png)

进去之后，将生成的内容复制进去，点击`Add SSH key`。

![配置ssh2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E9%85%8D%E7%BD%AEssh2.png)

至此，ssh的配置就完成了，接下来就需要配置一下git。

##### 配置git

进入终端，执行以下命令

```
# 配置用户名
git config --global user.name "Your Name"
# 配置邮箱
git config --global user.email "Your Email"
```

> 如果你有多个git账号，可以不加`--global`这个属性，不加这个属性就不会全局应用。

##### 测试

当我们全部都弄完之后，进入终端执行以下命令，查看返回的信息。

```
ssh -T git@github.com
```

![git身份验证](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/git%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81.png)

当返回如下信息，就证明配置成功了。

#### 上传文件

##### GitHub Pages部署

将本地的文件部署到GIthub，需要先修改根目录下的`_config.yml`文件，滑到最底部，修改`deploy`。

![上传配置1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E4%B8%8A%E4%BC%A0%E9%85%8D%E7%BD%AE1.png)

修改之后，还需要安装一个插件才能上传

```
npm install hexo-deployer-git --save
```

安装玩插件之后，执行以下命令即可完成。

```
# 清除缓存
hexo clean
# 重新生成文件
hexo g
# 发布
hexo d
```

完成之后，在浏览器中输入`https://your.github.io`，查看是否发布成功。

![github.io](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/github.io.png)

##### 源文件上传

源文件上传就比较简单了，直接根据仓库给出的命令执行一次即可。

![仓库上传文件步骤](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse/Hexoimage/%E4%BB%93%E5%BA%93%E4%B8%8A%E4%BC%A0%E6%96%87%E4%BB%B6%E6%AD%A5%E9%AA%A4.png)

如果你想要从github中下载源文件使用，只需要`git clone 项目地址`，下载下来之后使用 `hexo init` 格式化文件夹和`npm install`下载依赖。

到此，这篇文章的内容就结束了。



<本文完>



> 本文参考文档[ConstOwn](https://blog.juanertu.com/archives/e3dc5cbb.html)

