# 个性化个人博客之音乐播放器


## 前言

我们创建好个人博客之后，或许我们会觉得只是纯文本阅读太过于的单调了，如果这时候可以有音乐播放就更好了，如果你有这方面的需求，那么就请跟我一起来进行简单的代码来实现这个需求吧。

> 本文博客是基于hugo搭建，不确保是否支持其他类型的，例如hexo。

## 具体流程

### 第一种方法

首先声明该方法不能实现音乐播放器一直显示在页面上，只有滑动到特定区域才可以显示出来，例如我将其插入博客页面的最底部，那么该播放器也只会出现在底部，不会出现在其他的地方。

```html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=110 src="//
music.163.com/outchain/player?type=0&id=2896870368&auto=1&height=90"></iframe>
```

> 特别提醒的是，我们可以根据实际情况修改width和height的值，如果当你出现播放器与侧边栏的菜单图片有冲突的话，可以考虑将`border`的参数删除试试。

#### 如何更换歌曲

更改歌曲只需要将代码中的`music.163.com/outchain/player?type=0&id=2896870368`后面的数字`2896870368`换成你自己的id。

#### 获取歌曲ID

如何找到这个id，需要你进入网易云官网，搜相关的歌曲，截取`playlist?id`后面的数值

![image8-1](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-1.png)

> 此方法不适用添加单独的歌曲！！！

#### 实现效果图

![image8-2](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-2.png)

### 第二种方法

首先声明该方法是在博客的底部添加音乐组件，并且可以自定是否自动播放和是否开启歌词功能以及是否固定在左下角不动。

```html
<!-- 为博客底部添加音乐组件 -->
<div id="player"  class="aplayer"></div>
<link href="https://files.cnblogs.com/files/shwee/APlayer.min_v1.10.1.css" rel="stylesheet">
<script src="https://files.cnblogs.com/files/shwee/APlayer.min_v1.10.1.js"></script> 
 
<script type="text/javascript">
var ap = new APlayer({
    element: document.getElementById('player'),
    narrow: false,
    autoplay: false,          <!-- 是否自动播放 -->
    showlrc: true, <!--是否开启歌词功能 ，默认false（为true时musics集合中需要传入lrc字段。）-->
    fixed:1,<!-- 是否固定在左下角不动， 1即为true -->
    theme: '#F5F5F5',      <!-- 插件背景颜色，建议和你的公告栏背景色一样，这样融为一体的感觉 -->
    music: [{
            title: '那些花儿',
            author: '朴树',
            url: 'http://music.163.com/song/media/outer/url?id=28996922.mp3',
            cover: "http://p2.music.126.net/j1EJGPJ0WaudM0DBSDCY8w==/109951168111041972.jpg",
            lrc:"[00:00.000] 作词 : 朴树[00:01.000] 作曲 : 朴树[00:17.36]那片笑声让我想起[00:20.72]我的那些花儿[00:24.38]在我生命每个角落[00:28.21]静静为我开着[00:32.21]我曾以为我会永远[00:36.01]守在她身旁[00:40.11]今天我们已经离去[00:43.85]在人海茫茫[00:47.08]她们都老了吧?[00:50.76]她们在哪里呀?[00:55.23]幸运的是我[00:58.83]曾陪她们开放[01:02.99]啦.....想她[01:10.67]啦.....她还在开吗?[01:18.43]啦.....去呀[01:26.38]她们已经被风吹走[01:30.12]散落在天涯[01:33.22][01:49.61]有些故事还没讲完[01:53.47]那就算了吧[01:57.16]那些心情在岁月中[02:01.06]已经难辨真假[02:05.21]如今这里荒草丛生[02:09.06]没有了鲜花[02:13.04]好在曾经拥有你们的春秋和冬夏[02:20.29]她们都老了吧?[02:23.85]她们在哪里呀?[02:28.54]幸运的是我曾陪她们开放[02:35.83]啦.....想她[02:43.54]啦.....她还在开吗?[02:51.28]啦.....去呀[02:59.42]她们已经被风带走[03:03.20]散落在天涯[03:06.82]啦……[03:14.54]啦……[03:22.42]啦……[03:30.02]……[04:01.98]人们就像被风吹走插在了天涯[04:08.66]她们都老了吧?[04:12.26]她们还在开吗？[04:16.74]我们就这样[04:20.74]各自奔天涯[04:25.16]"
        }
    ]
});
ap.init();
</script>
```

> 使用该方法添加音乐的方法跟上面是一样的，也是获取歌曲的ID，需要注意的是该方法是不适用添加歌单的。

#### 如何获取lrc歌词

获取lrc歌词的方法有很多，在这里我推荐两种获取的方法，第一种打开浏览器进入这个网页[lrc歌词获取](http://music.163.com/api/song/media?id=)，将我们需要获取lrc歌词的歌曲ID复制进去，就像这样。

![image8-9](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-9.png)

另外一种就是到这个网址[lrc歌词编辑器](http://lrc.opqnext.com/)里面去搜索，这里面的所有数据均是来自于网易云。

#### 实现效果图

![image8-3](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-3.png)

### 第三种方法

首先声明该方法功能强大，适用多种模式，并且自动识别歌词，不需要我们手动添加lrc歌词了。

```javascript
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/aplayer@1.10.0/dist/APlayer.min.css">
<script src="https://files.cnblogs.com/files/wkfvawl/APlayer.min.js"></script>
<div id="aplayer" class="aplayer"  data-id="7008690471" data-server="netease" data-type="playlist" data-fixed="true" data-listfolded="true" data-order="random" data-theme="#F58EA8"></div>
<script src="https://unpkg.com/meting@1.2/dist/Meting.min.js"></script>
```

> 需要注意的是，如果你复制上面的这一串代码，但是没有在博客左下角显示的话，建议修改`data-id`的值。如果你想根据下面的代码进行自定义，需要在前面加上`data-`，例如实现自动播放，需要写成`data-autoplay="true"`。

```html
一些参数
    mini: false, //迷你模式
    autoplay: false, //自动播放
    theme: '#FADFA3', //主题色
    loop: 'all', //音频循环播放, 可选值: 'all'全部循环, 'one'单曲循环, 'none'不循环
    order: 'random', //音频循环顺序, 可选值: 'list'列表循环, 'random'随机循环
    preload: 'auto', //预加载，可选值: 'none', 'metadata', 'auto'
    volume: 0.7, //默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
    mutex: true, //互斥，阻止多个播放器同时播放，当前播放器播放时暂停其他播放器
    listFolded: false, //列表默认折叠
    listMaxHeight: 90, //列表最大高度
    lrcType: 3, //歌词传递方式
```

> 想要自动播放的话，就添加data-autoplay="true"到第三行代码div后面，同时`server `可选 netease（网易云音乐），tencent（QQ 音乐），kugou（酷狗音乐）。`type`可选 song（歌曲），playlist（歌单），album（专辑），search（搜索关键字），artist（歌手）;

#### 实现效果图

##### 歌单

如果想要设置歌单播放的话，只需要修改第三行div中的`data-type`为`"playlist"`即可，同时记得修改`data-id`的参数为你自己歌单的ID，获取ID的方法跟前面的一样。

![image8-4](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-4.png)

##### 单曲

如果想要自己设置歌曲播放的话，只需要修改第三行div中的`data-type`为`"song"`即可，同时记得修改`data-id`的参数为你想要的歌曲的ID，获取ID的方法跟前面的一样。

![image8-5](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-5.png)

##### 专辑

如果想要设置专辑播放的话，只需要修改第三行div中的`data-type`为`"album"`即可，同时记得修改`data-id`的参数为你想要的专辑的ID，获取ID的方法跟前面的一样。

![image8-6](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-6.png)

##### 搜索关键词

如果想要设置搜索关键词播放的话，只需要修改第三行div中的`data-type`为`"search"`即可，同时记得修改`data-id`的参数为你想要的搜索的关键词，例如想要搜索`空空`，就只需要将`空空`放进`data-id`中即可。

![image8-7](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-7.png)

##### 歌手

如果想要听某一位歌手的全部音乐，需要修改第三行div中的`data-type`为`"artist"`即可，同时记得修改`data-id`的参数为歌手的ID，获取歌手ID的方式跟前面的差不多，只是需要我们点进歌手的主页，复制`artist?id`后面的数值即可实现。

![image8-8](https://cdn.jsdelivr.net/gh/qichenxiaoni/Picture-warehouse@main/img/image8-8.png)

> 网易云音乐支持以上五种不同的方式，酷狗支持搜索关键词，建议使用网易云，同时提醒不管使用任何音乐平台，都存在VIP歌曲无法听的现象或者是VIP歌曲只能听60S。

### 总结

上面三种不同的方法都可以实现博客音乐播放器，但他们效果、样式以及使用效果各有不同，按需使用，不管歌单还是歌曲尽量使用网易云音乐，因为网易云音乐的id没有被隐藏，其他例如QQ音乐和酷狗音乐的歌曲id被隐藏了。



<本文完>



> 本文参考[官方教程](https://aplayer.js.org/#/zh-Hans/)，以及[博客园添加背景音乐以及播放器 或在左下方固定位置添加音乐播放器 给你的博文锦上添花，增姿添彩](https://blog.csdn.net/q1246192888/article/details/111409908)

