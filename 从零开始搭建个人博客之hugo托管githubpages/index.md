# 从零开始搭建个人博客之hugo托管GitHubPages


## 前言

[Hugo](https://gohugo.io/)是一款快速，现代化且高度可配置的静态网站生成器。它是一个基于命令行的工具，用于将Markdown等文本格式转换为静态网站。Hugo使用Go语言编写，因此它非常快。Hugo的主要优点是构建速度非常快，因为它是一个静态网站生成器，没有必要运行数据库或其他服务。

使用Hugo创建个人博客的主要优势在于它非常快速、易于配置，并且生成的网站可以直接部署到任何Web服务器上，而不需要运行数据库或其他服务。此外，Hugo提供了大量的主题和插件，可以轻松地自定义您的个人博客。它还支持各种文本格式，包括Markdown，AsciiDoc和Org-mode，以及多种语言，包括中文。

## 整体流程

1. 写 Markdown 文件；
2. 通过 hugo 架构提供的语法将 Markdown 文件编译成 HTML 文件，HTML文件就是在浏览器中可以展示的文件格式；
3. 把编译出来的 HTML 文件发布到服务器或者网站托管平台；

我们可以通过上面简单的三步骤生成一个只属于自己的个人博客，是不是感觉非常的简单呢，那跟着我一起来使用 hugo 搭建一个属于自己的个人博客吧。

## 具体流程

在上一篇博客中，我们已经简单的学习了一下如何搭建个人博客，在这一篇博客中，我们来学习一下如何将我们搭建的个人博客托管到 GitHub Pages 中，首先我们先来了解一下什么是 GitHub Pages。

GitHub Pages 是一项服务，它允许用户将静态网站托管在 GitHub 上。用户可以使用 GitHub Pages 来托管个人博客、项目文档、用户手册等等。GitHub Pages 支持多种静态网站生成器，包括 Jekyll、Hugo、Hexo 等等。它还提供了自定义域名的选项，因此用户可以使用自己的域名来访问他们的网站。GitHub Pages 是完全免费的，但是需要遵守GitHub的使用规则和政策。

我们了解了什么是 GitHub Pages 之后，那么我们为什么要放到 GitHub Pages 里面呢，是因为我们现在搭建的仅仅只是能使用在自己的电脑中，如果换一个电脑之后，我们就不能访问了，因此我们需要一个托管平台，因此我们就将文件托管到 GitHub Pages 中。

现在我们已经了解了原因之后就开始今天的学习吧。

### 创建 GItHub Pages

首先要想使用 Github Pages，就必须要有一个 GitHub 账号，如果没有 Github 账号，可以[点击此链接](https://www.github.com)跳转注册一个。

当我们登录 Github 之后，点击 New 创建一个新的 Repository ，命名为 {your_username}.github.io ，记住，这里的名字一定是你的用户名，如果不是的话，会无法进行下一步操作。

![image2-1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2-1.png)

因为我这里已经创建好了，因此它会报问题，格外需要注意的是 Repo 的权限一定是要 公开的，也就是一定要选择 Public ，因为如果选择了 Private ，后面就会出现无法访问的问题，同时也可以勾选上 `Add a README.md` ，这样做的原因是为了自动创建 main 分支。

然后找到你刚刚创建好的仓库，点进去，选择上面的 Settings ，在左边的菜单栏中选择 Pages ，如果跟我的不一样，没有关系，这是因为 Github Pages 还在自动帮我们部署网站，只需要稍等片刻即可。

![image2-2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2-2.png)

当你看到你的 Page 页面上出现 Your site is live at https://********.github.io/ 时就说明你的 GitHub Pages 自动部署好了，这时点击 Visit Site 就可以看到我们的网站了，当然了因为这时候我们的仓库中空的，所以这时候的网站也是空的，只会显示 yourusername.github.io 。

### 搭建 Hugo 站点

#### Hugo 站点和目标文件

现在我们有了`Hugo`个人站点，有了`Github Pages`，那么下一步就是把 hugo 博客发布到 GitHub 。这样我们才能在互联网的任何地方访问我们的博客。

在我们本地的 Hugo 根目录中执行 Hugo 指令。会生成一个 Public 文件夹，我们只需要把 Public 的文件夹上传到 Github 上刚才创建的`Github`仓库里面, 一分钟左右，就能正常查看博客内容。

> hugo 站点（ hugo 根目录）：这个是源文件，也就是你写 Markdown 的地方，可以不用提交到GitHub，也可以选择在 GitHub 上创建一个新的 Repo ，并提交。                 
>
> public 文件（ hugo/public ）：这个是目标文件，是使用 hugo 指令生成的发布 HTML 内容，可以在浏览器浏览的格式，需要推送到 GitHub 上然后发布到 GitHub Pages 静态网站。

我们的Hugo站点是**源文件**（带主题、图片、Markdown 源文件），public 是**目标文件**（最终生成的 css/js 或者是 html 文件）。我们最终需要在网页上展示的是目标文件，所以我们需要使用 Hugo 命令生成目标文件。

#### 将博客部署到 GitHub Pages

在任何 Hugo 站点外（也就是根目录的上级目录处，为什么要出根目录之外进行，是因为方便我们之后将源文件也上传到 GitHub 一份，Git 是不能有层级的，因此我们需要放到站点外面），直接用 Git Clone 将创建好的 `GitHub仓库`克隆上来。

```shell
cd ../
git clone git@github.com:qichenxiaoni/qichenxiaoni.github.io.git
```

**复杂一点但是后续方便的办法：** 为了不要每一次改动之后都要手动复制一次，我们可以创建一个 public 目录和 GitHub 仓库的软链接（需要注意的是我们需要先删除根目录下的 public 文件夹）

```shell
# 进入 Hugo 根目录
cd ~/Docments/Code \ TMP/qichenxiaoni
# 删除 public 文件夹
rm -rf public
# 前面是 GitHub.io 仓库，后面是 public 文件的本地目录
ln -s ~/Documents/Code\ TMP/qichenxiaoni.github.io ~/Documents/Code\ TMP/qichenxiaoni/public
```

然后在`hugo站点`使用 hugo 指令，就会自动在 public 软链接也就是 git repo 下生成目标文件。

最终执行`git add/commit/push`之后，打开 https://qichenxiaoni.github.io/ 就能看到博客内容。 (可能有几分钟延迟，耐心等待)。

![image2-3](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2-3.png)

当我们修改了博客的内容时，如果我们没有脚本来自动上传，那么我们可以执行以下命令来上传更新博客。

```shell
详细步骤：

cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ hugo

cd ~/Documents/Code\ TMP/qichenxiaoni.github.io/

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ ls  #(这一句可要可不要)

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ git status

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ git add *

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ git status

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ git commit -m "two commit"

cn@Resucer:~/Documents/Code TMP/qichenxiaoni.github.io$ git push
```

如果在执行`Git commit -m “first commit”`的时候报错，显示作者身份未知，显示如下信息的时候，我们可以根据上面的提示，分别执行下面这两条命令之后再执行一次`Git commit -m “first commit”`

![image2-4](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2-4.png)

```shell
git config --global user.email "you@example.com"(注册GitHub的邮箱)
git config --global user.name "Your Name" (Github的用户名)
```

如果在执行 Git Push 的时候报错显示没有权限

```
ERROR: Permission to left-pocket-test/left-pocket-test.github.io.git denied to left-pocket.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
```

解决的办法十分的简单，只需要我们在 GitHub 中添加一下密钥文件就可以了，接下来我会给出在 Linux 中和 Windows 和 Mac 中如何生成密钥文件

首先是在 Linux 中：

```shell
cd ~/.ssh
ssh-keygen -t rsa -C "xxx@xxx.com" #填写自己的邮箱地址
#之后按Enter一直回车即可
cat ~/.ssh/id_rsa.pub
#复制里面的内容粘贴到github中即可(点击右上角头像Settings->SSH and GPG Keys->add SSH Key.)
```

在 Windows 和 Mac 中：

```shell
1. 在 Windows 中打开 Git Bash 终端。
2. 在终端中输入以下命令，并按 Enter 键：
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
这个命令会创建一个新的 SSH 密钥文件，您需要将 "your_email@example.com" 替换为您自己的电子邮件地址。
3. 然后，您将被要求输入一个文件名，用于保存密钥文件。您可以接受默认文件名，或者指定一个您自己喜欢的名称。
4. 接下来，您将被要求输入一个密码短语。这个密码短语将加密您的私钥，确保只有您可以访问它。当您输入密码短语时，终端不会显示任何内容，所以请确保您输入的正确。
5. 最后，您将获得一个公钥和一个私钥文件。您的公钥文件将位于 "~/.ssh/id_rsa.pub"，您的私钥文件将位于 "~/.ssh/id_rsa"。请注意，您的私钥文件必须始终保持机密，所以请确保将其保存在安全的地方。

如果是 mac 的话，步骤跟 windows 的是一样的，这里就不重复说明了。

当我们生成密钥文件之后，回到 Github 中，点击右上角的头像，找到Settings，找到左边菜单栏中的`SSH and GPG keys` ，选择`New SSH key`，将密钥文件的内容复制进去即可。
```

#### 将源文件上传到 GitHub

为什么我们要将源文件发布到Github中呢，是因为防止本地电脑的硬盘损坏或者文件丢失等风险，因此我们可以在Github中新创一个仓库用来保存源文件，同时如果以后个人博客需要多人的时候也支持多人协作，当然了源文件对于最后的成品展示没有任何影响，简而言之就是如果有需求的可以跟着弄一遍，如果没有这方面需求的，可以直接跳过。

步骤跟前面创建Repo是一样的，只是名称可以随意改动，不需要勾选生成README.md文件，由于我们没有选择生成文件，因此这时候的仓库是没有任何东西的，同时创建完之后GIthub也会提醒你如何使用指令将本地内容上传至Github中。

**具体步骤：**

```shell
#在源文件目录（就是后面不带github.io）
echo "# qichenxiaoni.github.io" >> README.md
git init
git add *
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:qichenxiaoni/qichenxiaoniio.git
git push -u origin main
```

如果你在执行`Git add *`这一条指令的时候出现这一类消息的时候，可以使用 git status ，如果执行完 git status 之后，显示有未跟踪的文件，可以单独使用`git add ‘文件名’`

![image2-5](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image2-5.png)

这个时候你的源文件就上传到Github的一个新的仓库了。这是用来保存源文件的。而**{your_username}.github.io**是用来保存网站的目标文件的。

由于有人不了解如何在修改了源文件之后保存到Github中，因此下面是具体步骤：

```shell
#当修改了源文件需要保存的时候，详细步骤：
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ hugo new about/index.md
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ git status
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ git add *
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ git status
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ git commit -m "two commit"
cn@Resucer:~/Documents/Code TMP/qichenxiaoni$ git push
```



<全文完>



> 本文参考教程：[码农在新加坡的个人博客](https://www.leftpocket.cn/post/hugo/hugo_github/)
