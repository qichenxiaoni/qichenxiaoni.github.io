# Notion创建个人博客之创建个人主页


## 前言

当今个人博客盛行，人们都想要有一个属于自己的个人博客，但是很多人苦于没有编程基础或不想使用代码来制作一个个人博客，但好在现在有一种方式可以不用敲一行代码就可以制作出一个属于自己的个人博客，只需要有一个Notion账号，Github账号以及Vercel账号就可以实现了。那么废话就不多说了，开始本次的教程吧！

## 背景知识

1. [**Notion账号**](https://www.notion.so/)：Notion是一款功能强大的效率软件，现在也有很多的使用量，它在日常中极大的方便了我们的生活，提高了我们的效率，以及能很好的帮助我们管理我们的日常生活、学习以及工作中的等等事项，并且它也支持团队协作，是一款不可多得的好软件。
2. [**Github账号**](https://www.github.com)：个人网站的主题是通过Github的NotionNext 项目来实现和配置的，有着丰富的展示效果，比如布局，主题，文章目录，添加音乐，评论系统等等。
3. **[Vercel账号](https://vercel.com)**：是一个托管平台，负责部署NotionNext项目，来最终显示你的个人网站。

## 具体操作流程

### 获取模板

首先我们需要有一个Notion账号，在浏览器中输入notion的官网地址：https://notion.so/登录，如果没有账号的，也可以在此页面进行注册（注册可以用自己的email地址也可以使用goole账号进行注册）之后再登录。

登录之后，打开[**notion模板**](https://www.notion.so/34889e026fc44f7eb074c3847a052020)获取模板文件，点击进去之后我们可以看到

![image5-1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image5-1.png)

点击框起来的链接，这时会跳转到模板页面，选择右上角的Duplicate，将模板克隆到自己的Notion账号中。

![image5-2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image5-2.png)

将模板克隆下来之后，我们可以直接点击页面右上角的Share，选择Share to web，也可以在进行修改之后再发布出去。

### 模板解释以及模板操作

在修改模板文件之前，先简单的介绍一下各列的意思

1. `type`:在这一列中，Post表示博客，Page表示菜单，包含归档、留言以及友链等等，Notice表示公告；
2. `status`：在这一列中，Published表示已发布出去的，Invisible表示不可见的，Draft表示草稿，我们可以根据这个来自由的修改文章的状态；
3. `title`：在这一列中，我们可以进行简短的文章介绍，点击Open就可以打开页面进行编辑；
4. `slug`：这一列是指链接后缀名，因为不填写这个，notion就会随机生成一个字符串，随机生成的字符串杂乱无序，不方便我们阅读,当然了，一定不能重复，一旦重复就会重复显示。

介绍完了主要的模板列的意思之后，那么就会有人问了，怎么添加新的页面呢？很简单，只需要我们点击下面的`+ New`就可以生成新的一行，也就是生成一篇新博客，然后只需要根据我们的需求来修改每一列的信息就好了，找到`title`列点击open就可以编辑博客的具体内容了，notion支持Markdown语法，同时它也支持“/”命令来进行更多的操作，例如生成待办事项、表格、插入链接等等。

制作好一遍新的博客，那怎么发布出去呢，我们可以直接点击右上角的share将页面发布出去，但是需要注意的是，这时候发布出去的页面是跟你编辑的页面一样的，也就是不会有任何的主题，也不支持域名自定义，因为这仅仅只是使用notion自带的页面分享功能，还需要github和vercel的支持。

![image5-3](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image5-3.png)

<本文完>

> 本文至此就结束了，如果还有不懂的可以看[码农在新加坡](https://www.leftpocket.cn/post/notion/blog/)的教程。

