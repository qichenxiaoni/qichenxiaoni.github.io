# 从零开始搭建个人博客之绑定域名


## 前言

[Hugo](https://gohugo.io/)是一款快速，现代化且高度可配置的静态网站生成器。它是一个基于命令行的工具，用于将Markdown等文本格式转换为静态网站。Hugo使用Go语言编写，因此它非常快。Hugo的主要优点是构建速度非常快，因为它是一个静态网站生成器，没有必要运行数据库或其他服务。

使用Hugo创建个人博客的主要优势在于它非常快速、易于配置，并且生成的网站可以直接部署到任何Web服务器上，而不需要运行数据库或其他服务。此外，Hugo提供了大量的主题和插件，可以轻松地自定义您的个人博客。它还支持各种文本格式，包括Markdown，AsciiDoc和Org-mode，以及多种语言，包括中文。

## 整体流程



1. 写Markdown文件；
2. 通过hugo架构提供的语法将Markdown文件编译成html文件，html文件就是在浏览器中可以展示的文件；
3. 把编译出来的html文件发布到服务器或者网站托管平台；

就上面的三步就可以生成一个个人博客，是不是非常的简单呢，那么，跟着我一起来使用hugo搭建一个属于自己的个人博客吧。

## 具体流程

在前面一篇文章中我们将文件托管到了Vercel，在这一篇文章中，我们需要使用域名来绑定个人博客，实现使用域名来访问博客的操作。

### 申请域名

获取域名的方式有两种，第一种就是付费域名（可以在浏览器中输入https://wanwang.aliyun.com/，也可以点击[阿里云](https://wanwang.aliyun.com/)，另一种就是免费域名（可以在浏览器中输入http://freenom.com/，可以点击[此链接](http://freenom.com/)跳转过去，需要注意的是Freenom现在服务器不稳定，不知道还能不能使用了，至少我这几天都无法使用。

使用阿里云的，需要注册登录之后，在域名注册页面上输入自己喜欢的名字，然后点击查询域名，下面就会出现很多域名以及价钱，有些域名已经被人注册了，尽量选择没有被注册的，当然也可以选择通过平台去购买那些被注册且注册者愿意出售的域名，选择好了之后就可以进行支付。

> 温馨提示：第一次购买域名，需要进行实名认证，并且还需要你制作一份模板进行审核，时间不确定，因为这份模板需要给注册局进行审核，因此时间不确定，可能二十多分钟就可以了，也可以一个多小时，第二次购买的时候也需要进行实名认证，但是时间会短一些，十分钟左右就可以了。

使用Freenom的，也需要注册登录，在登陆之后点击Service ->Register a New Domain，然后输入你想要注册的域名，点击Check Availability，然后进行购买。

> 温馨提示：Freenom的最长免费期限是一年，选择Checkout，然后选择免费期限，点击购买，即可成功购买。

### DNS解析

虽然我们已经购买了域名，但是我们依旧需要进行域名解析之后才能够使用。如果我们是在阿里云上购买的话，阿里云自身就配有域名解析，因此我们可以直接找到域名解析进行操作。

#### 绑定 Vercel （阿里云）

在阿里云上进行域名解析需要我们进行域名列表，找到我们想要解析的域名，选择解析操作，这里可能会存在一个问题就是域名的状态显示有问题，一般都是因为DNS服务器设置不正确，它会给出两个正确的DNS服务器，不过一般来说不会出现这个问题，如果出现问题了可以先刷新然后看是否解决了，如果没有解决就根据上面给出的DNS进行修改。

当我们的域名状态显示是正常的，就可以点击操作下面的解析，然后添加记录。

![image4-1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4-1.png)

绑定Vercel需要两条记录，一条A记录，一条CNAME记录，回到Vercel，点进刚刚弄好的项目选择上方的Settings，找到Domains，添加我们刚刚申请好的域名，这时候Vercel会提示我们添加一个A记录和CNAME记录。

![image4-2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4-2.png)

![image4-3](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4-3.png)

回到阿里云的域名解析页面，添加这两条记录。首先是添加A记录

![image4-4](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4-4.png)

添加完A记录之后添加CNAME记录

![image4-5](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image4-5.png)

至此，我们就添加好了，可以等待几分钟，让Vercel部署好之后，使用刚刚的域名进行访问。

#### 绑定Vercel（Freenom）

由于Freenom里面没有配有DNS解析服务，因此我们选择DNSPod这款产品来进行域名解析，这一款产品是腾讯云旗下的品牌，可以使用腾讯登录。

登录之后选择管理控制台->DNS解析->我的域名->添加域名，会提示需要设置正确的DNS服务器，因为你的域名没有设置DNS服务器，也就是没有授权DNS服务器解析你的域名。

当提示需要设置正确的DNS服务器，这里是需要回到刚才的购买域名的网站freenom来绑定域名解析的地址。（绑定了之后才能授权DNSPod解析你的域名），点击 `My Domains`>`Manage Domains`>`Management Tools`>`Nameservers`。

回到`dnspod`, 重新验证，状态会变成无记录。意味着域名和DNS服务商已经绑定成功。

现在域名设置成功了，还没有域名解析记录。

域名绑定到网站需要添加两条记录，一条`A`记录，一条`CNAME`记录。

回到你的vercel，点击你的项目->`Settings`>`Domains`

添加你刚申请的域名，会提示你添加一条A记录和CNAME记录，这时候我们回到DNSPod，添加这两条记录即可，添加过程跟阿里云的大同小异。添加完之后，等待几分钟，让Vercel自动部署一下，直接输入域名进行测试。

然后你尝试使用域名去访问，如果正常显示，就说明已经成功了，如果显示错误，请重新检查一遍。

至此，个人博客就成功搭建。



<本文完>



> 本文参考教程：[码农在新加坡的个人博客](https://www.leftpocket.cn/post/hugo/hugo_dns/)

