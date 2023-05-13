# 从零开始搭建个人博客之使用hugo创建个人站点

## 前言

[Hugo](https://gohugo.io/)是一款快速，现代化且高度可配置的静态网站生成器。它是一个基于命令行的工具，用于将Markdown等文本格式转换为静态网站。Hugo使用Go语言编写，因此它非常快。Hugo的主要优点是构建速度非常快，因为它是一个静态网站生成器，没有必要运行数据库或其他服务。

使用Hugo创建个人博客的主要优势在于它非常快速、易于配置，并且生成的网站可以直接部署到任何Web服务器上，而不需要运行数据库或其他服务。此外，Hugo提供了大量的主题和插件，可以轻松地自定义您的个人博客。它还支持各种文本格式，包括Markdown，AsciiDoc和Org-mode，以及多种语言，包括中文。

## 整体流程

1. 书写Markdown文件；

2. 通过hugo架构提供的语法将Markdown文件编译成HTML文件，HTML文件就是在浏览器中可以展示的文件；

3. 把编译出来的HTML文件发布到服务器或网站托管平台；

我们可以通过以上简单的三步实现生成一个只属于自己的个人博客，是不是非常的心动呢？现在就跟着我一起来使用hugo搭建一个直属于自己的个人博客吧。



## 具体流程

### 安装hugo

首先需要特别说明的是，我是在Linux系统环境下安装的Hugo，不同的系统安装有不同的方法，此方法不一定适用于所有系统，如遇不适用，烦请各位自行搜索。

```shell
# 安装hugo
sudo apt install hugo
#查看版本
hugo version
```

> 更新：需要注意的是，ubuntu22.04.2系统中安装hugo个人博客时使用该教程中的主题，只能使用`sudo apt install hugo`，不能使用deb包。

![image1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image1.png)

### 创建站点

```shell
# 要存放文件路径下，例如我是在Docments创建的，因此我就要进入Docments
cd ~/Docments/Code \TMP
执行hugo创建文件夹的命令
hugo new site qichenxiaoni
进入刚刚创建好的文件夹中
cd qichenxiaoni
查看里面的文件
ls
```

![image2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2.png)

**简单的介绍一下目录中的部分文件**：

**config.toml** 是配置文件，在里面可以定义博客地址，构建配置，标题，导航栏等等。

**themes**是主题目录，可以下载喜欢的主题，然后配置在***\*config.toml\****里面。

**content**是博客文章的目录。

**static**是博客的静态资源，比如图片

**public**是编译后的目标文件的目录。

> 格外需要注意的是，现在我们进入的目录就是我们的根目录，里面存放的是你这个博客的所有源文件，也就是Markdown文件、模板文件以及配置文件和你所需要的图片。其次，最终呈现在网页上的不是你的Markdown文件，而是Markdown文件被编译生成的HTML文件，如果你使用F12打开开发人员模式就可以看到里面使用的CSS和JS部分。

### 设置主题

在我们的博客正式运行之前，我们需要给博客设置一个主题，官方主题网站中有很多的主题文件。可以[点击此链接跳转](https://themes.gohugo.io/)，在这里我使用的主题文件是[~~Even~~](https://github.com/olOwOlo/hugo-theme-even)（后面我更改了主题，但是在这一系列的教程中还是使用的是Even）

#### 安装主题

需要特别注意的是，这时候我们是要在根目录下运行这行指令，也是要在站点目录下运行，例如我的站点就是qichenxiaoni，因此我要在qichenxiaoni这个路径下执行指令

```shell
git clone https://github.com/olOwOlo/hugo-theme-even /themes/even
如果你没有安装git命令可以先去安装git
sudo apt install git
```

> 如果这时候你发现 git 的速度很慢或者是显示连接超时，可以在 git 前面加上一个 sudo，（此方法用于 Linux）如果还是不行，可以选择手动下载主题，然后复制到根目录下的 themes 目录中，不过可能会报‘WARN 2021/02/03 10:56:17 found no layout file for "HTML" for kind "home": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.’，这时候我们需要重新 git clone 一下主题。

#### 配置主题

使用VSCode或者WebStorm等代码编辑器打开主题的`exampleSite`目录下找到一个名为`confiig.toml`配置文件，打开这个文件，将里面的内容都复制到你根目录下的`config.toml`文件中，然后根据注释进行修改自定义，下面是我做的一些简单修改，可以简单参考一下。

```toml
languageCode = "zh-cn"
defaultContentLanguage = "zh-cn"                             # en / zh-cn / ... (This field determines which i18n file to use)
title = "小陈的博客"

[author]                  # essential                     # 必需
  name = "Chen"

[sitemap]                 # essential                     # 必需
  changefreq = "weekly"
  priority = 0.5
  filename = "sitemap.xml"

[[menu.main]]             # config your menu              # 配置目录
  name = "主页"
  weight = 10
  identifier = "home"
  url = "/"
[[menu.main]]
  name = "归档"
  weight = 20
  identifier = "archives"
  url = "/post/"
==[[menu.main]]
  name = "标签"
  weight = 30==
  identifier = "tags"
  url = "/tags/"
[[menu.main]]
  name = "分类"
  weight = 40
  identifier = "categories"
  url = "/categories/"

logoTitle = "小陈的博客"        # default: the title value    # 默认值: 上面设置的title值
```

至此我们也就完成了基本的配置，此时的博客也已经初具雏形了，如果后续需要修改，也可以根据config.toml文件里面的注释进行修改，接下来我们需要尝试创建一个博客页面，来看看我们修改的最终成果如何。

#### 创建第一篇博客

使用以下命令创建出第一个个人博客内容页面吧

```shell
hugo new post/first-post.md
```

需要注意的是，我们所有的markdown源文件都在根目录下的`content/post`下，不过post文件夹一般都不存在，因此我们在第一次创建的时候需要先创建这个文件夹，以后在创建新的博客时也需要加上这个文件夹，不然他不会创建到这个文件夹中的。

> 当我们生成了新的 md 文件时，它会自动生成一些行，我们可以看到它的 draft 选项后面接的是 true，当它是 true 的时候是默认不渲染的，如果需要渲染的话，我们可以将 true 改成 false，这样就可以渲染了，但是我们在这里直接将 draft 选项注释掉，然后加上 markdown 语法就 OK 了。后续可以直接自己直接在编辑器里面。

![image3](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image3.png)

**温馨提示：** 如果我们需要在博客中插入图片的话，我们需要在static目录下创建存放图片的文件，一般会命名为image或是img。

#### 发布博客

当我们完成上述的操作之后，我们还缺一个步骤就可以完成啦，那就是将我们创建好的博客发布出去，那么怎么发布呢，我们只需要执行一句简单的命令就可以啦。

```shell
hugo server
```

![image4](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4.png)

如果我们执行 `hugo server` 没有报错的话，就说明发布成功，我们就可以在浏览器中输入 `localshot:1313` 来查看我们的第一篇博客啦。

![image5](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image5.png)

至此，个人博客就初步的搭建出来了，你也可以自己去尝试一下通过 config.toml 中的注释来修改一下主题的配置，例如将页面下面的图标改成自己需要的，不用担心需要重新启动 hugo，因为 hugo 是立即生效的。

下一篇具体讲述如何将hugo博客托管到github pages中，为什么要托管到github pages的原因。



<全文完>



> 本文参考教程：[码农在新加坡的个人博客](https://leftpocket.cn/post/hugo/hugo_creation/)
