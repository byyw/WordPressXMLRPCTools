---
title: 【Markdown】Markdown语法与Typora编辑器
tags:
- Markdown
categories:
- 学习
---

# Markdown语法与Typora编辑器

> 此篇内容的来源为[苯苯-markdown](https://blognas.hwb0307.com/skill/1734)，为本人阅读完后再做整理分享。

## 前言

最初接触到**Markdown**还是在大学期间（18、19年），出于学习时做笔记的目的去了解的，同时也找到了当时最流行的Markdown编辑器**Typora**。

关于Markdown的介绍与优缺点，我就不多做说明，感兴趣可自行去搜索了解。虽然以往创作时很少采用Markdown，但我本身是很喜欢Markdown的。第一次接触Markdown时，就被写代码似的标记语言风格所吸引，相比同样是标记语言的html，使用起来十分轻便，仅简单的标记就能满足创作时大部分的需求。

虽然怎么说，但后续，学习笔记是没怎么写，最多的创作内容反而是日记、随笔。而出于云端同步的需求，另外选择了有道云笔记进行创作，并且文章格式也不是用Markdown，而是有道云默认的文章格式。故而到目前为止（2024-3-18），进行Markdown文章的创作次数屈指可数。

因为以往创作的内容是仅自己观看的，采用的是纯文本，写起来也十分随便。如今，出于想在个人博客上，记录并分享我生活、工作、学习的经历，对于文章的要求，就不再是只要自己看的懂就行，还需要适度的精炼与美化，而这方面，采用Markdown就可以轻松做到。

故此，写下这边文章，做以记录。

## Typora设置

### 主题

因为不想纠结，照着教程，直接使用[typora-vue-theme](https://github.com/blinkfox/typora-vue-theme)主题，操作如下。

首先，打开Typora主题文件目录，路径：***文件 -> 偏好设置 -> 外观 -> 打开主题文件夹（themes）***

![image-20240320092944079](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/image-20240320092944079.png)

之后将你从github上拉下来的主题文件中的css文件和对应的字体文件夹拷贝到themes下，再重启Typora

![image-20240320093341617](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/image-20240320093341617.png)

如果成功，在主题这边就会出现刚新添加的vue主题，选中后生效

**![image-20240320093917306](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/image-20240320093917306.png)**

### 自定义CSS

主要就两个文件，一个是全局的`base-control.css`，位于Typora安装路径下的`resources/style/`下，第二个是主题文件css，位于前文打开过的主题文件夹下对应css，比如当前我使用的是vue主题，所以对应的就是`vue.css`

base-control.css

![image-20240320095343351](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/image-20240320095343351.png)vue.css

![image-20240320095439684](C:\Users\byyw\AppData\Roaming\Typora\typora-user-images\image-20240320095439684.png)

之后可以根据你的使用习惯调整对应的css样式，比如想修改主题的加粗的颜色，可以在`vue.css`将`#write strong`中修改为：

```css
#write strong {
    padding: 0 1px;
    color: #CE7777;
}
```

### 快捷键

其实常用的功能就已经在Typora的导航栏就已经展示出来了

![image-20240320100420505](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/image-20240320100420505.png)

如果想自定义快捷键，可以在***文件 -> 偏好设置 -> 通用 -> 打开高级设置 -> conf.user.json***下进行编辑

## 基本Markdown语法

### 标题

``` markdown
# 一级标题
## 二级标题
### 三级标题，以此类推
```

### 列表

- 第一项
- 第二项

```markdown
- 第一项
- 第二项
```

### 备注

> 这里是备注内容

```markdown
> 这里是备注内容
```

### 高亮

常用的有**加粗**，*斜体*，`代码`

```markdown
**加粗**，*斜体*，`代码`
```

### 代码

除了在文本中用于高亮外，还能使用` ``` `插入整段代码，其中，`c`指定的代码块的语言是C语言

```c
printf("hello world");
```

````markdown
```c
printf("hello world");
```
````

### 链接

比如，[百度](www.baidu.com)

```markdown
[百度](www.baidu.com)
```

另外，Chrome浏览器有个[Copy as Markdown](https://chrome.google.com/webstore/detail/copy-as-markdown/fkeaekngjflipcockcnpobkpbbfbhmdn)的插件可以直接在网页上将链接复制为Markdown格式

### 图片

跟链接类似

```markdown
![75671183_p0_master1200](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/75671183_p0_master1200.jpg)
```

![75671183_p0_master1200](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/75671183_p0_master1200.jpg)

### HTML

简单来说就是Markdown支持html标签，比如

**字体**：

```html
<font face="黑体" color="#009688" size=10>只是因为在人群中多看了你一眼</font>
```

<font face="黑体" color="#009688" size=10>只是因为在人群中多看了你一眼</font>

**图片**：

```html
<img src="https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/03/22-52ce8992454cfb2bcbc065468f5db569-106035301_p0_master1200.jpg" border="0" />
```

<img src="https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/03/22-52ce8992454cfb2bcbc065468f5db569-106035301_p0_master1200.jpg" border="0" />

**表格**：

```html
<table><tr><td>排名</td><td>数据库</td><td>分数</td><td>对比上月</td><td>类型</td></tr><tr><td>1</td><td>Oracle</td><td>1221.06</td><td>-20.39</td><td>Relational</td></tr><tr><td>2</td><td>MySQL</td><td>1101.50</td><td>-5.17</td><td>Relational</td></tr><tr><td>3</td><td>Microsoft SQL Server</td><td>845.81</td><td>-7.76</td><td>Relational</td></tr><tr><td>4</td><td>PostgreSQL</td><td>634.91</td><td>5.5</td><td>Relational</td></tr><tr><td>5</td><td>MongoDB</td><td>424.53</td><td>4.18</td><td>Document</td></tr></table>
```

2024 年 3 月数据库排行榜

<table><tr><td>排名</td><td>数据库</td><td>分数</td><td>对比上月</td><td>类型</td></tr><tr><td>1</td><td>Oracle</td><td>1221.06</td><td>-20.39</td><td>Relational</td></tr><tr><td>2</td><td>MySQL</td><td>1101.50</td><td>-5.17</td><td>Relational</td></tr><tr><td>3</td><td>Microsoft SQL Server</td><td>845.81</td><td>-7.76</td><td>Relational</td></tr><tr><td>4</td><td>PostgreSQL</td><td>634.91</td><td>5.5</td><td>Relational</td></tr><tr><td>5</td><td>MongoDB</td><td>424.53</td><td>4.18</td><td>Document</td></tr></table>

**视频**：

```html
<iframe height="666" width="100%" src="//player.bilibili.com/player.html?aid=37070225&bvid=BV15t411X7Tn&cid=65141853&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
```
<iframe height="666" width="100%" src="//player.bilibili.com/player.html?aid=37070225&bvid=BV15t411X7Tn&cid=65141853&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## 小结

基本的说明就结束了，如果只是简单的使用，以上内容就足够了。当然除此之外还有更多高级的功能，比如数学公式LaTex、图表Mermaid等。有兴趣的同学可以自行深入了解。

写这篇文章的目的仅仅只是用于记录自身的学习足迹，便于自己回顾。除此之外，如果这遍文章能对你产生帮助，也不失为意外的收获，谢谢阅读。

## 参考

- [苯苯-markdown](https://blognas.hwb0307.com/skill/1734)
