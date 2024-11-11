---
title: 【Unity】Unity 引擎学习笔记
categories:
- 学习
- Java
---

# Unity 引擎学习笔记

## 前言

​	也许是自不量力了吧，毫无能力的我也想尝试做一款自己的游戏，讲述一个自己想讲的故事（不是他人想听的故事），为此投入自己虚度的时间，去学习独立游戏开发的一切所需的技能，仅我目前了解的，就包含策划、数值、文案、美术、音乐、程序、测试等，更何况还是我只有一个人的这种极端独立的情况。

​	想想都觉得不太可能。

​	理性看待，不仅自己的时间不够，而且就算成功了，也有后续的一系列问题接踵而来，运维、推广等等。而最终所得到的，大概率就是默默无闻，空耗时间而言。

​	在社会中，决定事物价值的，从来不是这件事物的难度，而是事物的供需。而我也就碌碌无为的一普通人，能力比我强的大有人在，资源比我充足的也如过江之鲫。在社会、历史这个背景板下，个人从来都不是特殊的，值得关注的始终是群体、趋势、大数据特征，在时代的浪潮下，所谓的弄潮儿，就算没有张三，也会有王五。

​	自怨自艾，怨天尤人罢了。如果我一怒之下，能把地球打爆，能有那么多破事，总归是实力不足而已。各种意义上的实力，个人能力，领导力，所有资源，等等等等。

​	牢骚了那么多，实际上这篇文也算是公开的（虽然没有人看），但一般这种比较负面的发泄，以往都是写在我的私有日记当中的，而自从我打算讲私有日记转为公开的博客之后，其实我自己写这些内容的频率也变得很少了，当然也有可能是因为正好接上我离职之后的摆烂时间。

​	那么，回归本文，想学习 Unity ，无非就是我有种想讲述什么的冲动而已，算是那种比较感性的人吧，经常性的会因为一些莫名其妙的事情产生一些情绪上的冲动，而我想做的，就是将那股瞬时的冲动记录下来而已。而与之相对的，记录的手段很欠缺，无论是在众生中都属下等的文笔（以高中作文的视角），还是学习的断断续续的画技（印象中，3年下来，仍然还在学素描），还有完全没入门的作曲。就连唯一能用来吃饭的技能，还是后端的 Java 开发，虽然也许有大神能用来讲故事，寄情于术，但愚笨的我始终无法达到。

​	总之就是，百无一用。

​	而游戏，就是以上的集大成者，我也不希望我一个人能做到人家几百人工业化的水准，仅仅只希望能自我满足就够了。

​	但还是得吃饭啊，所以，现在，就相当于在饿着肚子在这作为跳梁小丑而已。

​	另，学习的内容，是 B 站上UP[Gamer飞羽](https://space.bilibili.com/67744423)的[【Unity教程】零基础带你从小白到超神](https://www.bilibili.com/video/BV1gQ4y1e7SS/?spm_id_from=333.337.search-card.all.click)视频。

​	以上。

## 学习中

>  20241107，开始看视频，另，已经提前下载好了 Unity Hub 。

### 01 游戏引擎是啥玩意？

​	一本同作者的书《新印象 Unity 2020 游戏开发基础于实战》。

​	 简单介绍了下游戏引擎的概念，即游戏开发过程中常用到的轮子的集合。另外介绍了下 Unity 的特点，C# 开发，易上手，生态好，跨平台，等等。感觉某种程度跟 Java 的 Spring 类似，都仅仅只是调用人而已。

### 02 Unity，请说出你的优势

​	介绍了VR、AR、MR的相关概念，已经用 Unity 开发的一些比较知名的游戏。

### 03 动起来，下载与安装

> 20241108

​	从[Unity](https://unity.com/)官网上下载 Unity Hub ，这是 Unity 的版本管理工具，然后在Unity Hub 中下载标签为 LST 的稳定版本的 Unity，之后等待安装完成即可。

​	这一步照着视频来就行，基本不会出什么问题。

### 04 你好，编辑器

​	本节内容首先是创建一个空的 3D 项目，进入项目的开发界面后，再逐个介绍整个界面的菜单内容、配置、布局与窗口。因为我初接触，也不是很熟，这里就不多赘述了。另外，我在全程的学习过程中是准备全英文的，所以看起来比较费劲。但怎么说呢，英语，这个纠缠了我一生的学科，也是时候去面对了。

![Unity_pZolgJ2cYg](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/08-ef43e2892b6acc7f32f3e8b554692b79-08-ef43e2892b6acc7f32f3e8b554692b79-Unity_pZolgJ2cYg.webp)

### 05 迈出第一步，创建游戏物体

​	本届主要是熟悉了下如何创建 3D 对象（物体），也就是一些简单的几何体，分别为立方体（cube）、球（sphere）、胶囊（capsule）、圆柱（cylinder）、平面（plane）、四边形（quad）。做出如下图的效果我稍微调了下各物体的坐标与方向，果然在 2d 屏幕中整 3d 的东西还是有点难度的。

![Unity_WB8olh3PK6](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/08-43c7bb2691bdde1dd02d99e8a1d040f0-Unity_WB8olh3PK6.webp)

> 20241110

### 06 初中就学过？记录位置的坐标系

- x 横轴，y 纵轴，z 斜轴。

- 左手坐标系，z 轴正方向朝里；右手坐标系，z 轴正方向朝外。

- 全局世界坐标系，父物体的本地坐标系。

- 父子关系中，中心原点，轴心原点。

- 物体的移动操作杆，有相对世界方向的模式与相对物体方向的模式。

### 07 迟早用熟，对物体的基本操作

![Unity_BJuDQOrOAC](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-b746128edf86a0ac6a827c2a9bf08f06-Unity_BJuDQOrOAC.webp)

- View Tool，移动画面。

- Move Tool，移动对象。

- Rotate Tool，旋转物体。

- Scale Tool，缩放物体。

- Rect Tool，缩放物体（2d视图）。

- Transform Tool，综合工具。

- Edit bounding volume，编辑体积，用于碰撞？

​	另外，上述7个工具，对应的快捷键是Q、W、E、R、T、Y、U。

### 08 高大上了！快来导入游戏模型

​	主要讲的是资源的导入与导出。额外介绍了一些物体的渲染，材质（Shader），贴图的内容。

### 08.5 使用 blender 将 pmx 模型转为 fbx 并导入 Unity

​	因为想整这个东西，所以前后弄了快4个小时了，好在最后成功搞定了。那么，流程如下：

1、首先是从[模之屋](https://www.aplaybox.com/)中下载了一个模型，为 MMD 模型的荧宝，此时下载下来的模型格式为 pmx 格式。

![chrome_ute5hSXjcq](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-b6639442cb8eab5294e5a29ebc1e2641-chrome_ute5hSXjcq.webp)

2、之后选择一个 3D 建模软件，我这里选择了 [Blender](https://www.blender.org/)，并选择了 **4.2.3 LST** 版本进行安装下载。需要注意的是不同版本之间，其支持的插件也有些不同，就比如下一步说的 CATS ，而且在网上查找 Blender 的问题时，也需要注意对应的版本。

3、安装完成后，这时并不支持 pmx 格式的模型导入，所以需要往 Blender 中安装 CATS 插件。这个插件我找到的有两种，一种是支持 **Blender 2.93** 的 [CATS](https://github.com/absolute-quantum/cats-blender-plugin)，另一种是支持 Blender 更后面版本的 [CATS](https://github.com/teamneoneko/Cats-Blender-Plugin-Unofficial-)，选择的时候要注意版本匹配。

将插件下载到本地，下载成功后不需要解压，保持 zip 格式即可。之后进入 Blender 中，在 **Edit -> Preferences  -> Add-ons -> Install from Disk** 这个路径下，选中你下载到本地的插件压缩包，安装即可。

![](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-b887101220d6904063f6f0073514a76f-blender_QY4nNUnOu8.webp)

4、在 Blender 中，通过 **CATS -> Quick Access -> Import Model** 导入你下载的 pmx 模型。

![blender_U93S2JAJIF](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-17e487b4e2222f72cd6807bb67836245-blender_U93S2JAJIF.webp)

5、导入成功后，这时还是个白模，如果需要贴图，可以再右上角切换下显示，等待一会渲染出贴图。

![blender_zlma40t5ph](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-53952d6e0c4ef23806100c100dabc9c5-blender_zlma40t5ph.webp)

6、之后要将这个模型的所有部件的材质合并为一个。路径在 **CATS -> Optimization** 中。不过这时在 Optimization 栏目下会提示你安装一个新的插件，按照提示下载安装即可。之后通过 **Save Atlas to** 操作将所有材质合并为一个 png 图片材质。同时，荧的模型上的材质也会被替换，这时会出现因为透明度导致的色块呈黑块问题，特别在头发上。

虽然这是个【问题】，不过我暂时没去解决，等到后续学习 Blender 的时候再去关注下，现在还是先关注 Unity 吧。

![blender_B06L3NdlYe](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-3e0efc0e1624824fe0f4c53e26bcbe5f-blender_B06L3NdlYe.webp)

7、将模型导出为 fbx 格式。如果你们进行过操作6，会因为材质太多而导致导出时无法将材质一并导出，再导入到 Unity 中就只是白模了，这里卡了我好久。而且我感觉也不一定时材质数量的【问题】，应该还有那处没被我注意到的，还是留到后续再研究吧。

另，导出的路径在 **File -> Export -> FBX** ，在弹出的窗口选择导出路径，并配置导出选项。之后得到一个 fbx 文件与一个材质文件夹。

- Path Mode: Copy，表示会将材质资源一并导出，如果点上后面的文件夹图标，会将材质进一步包装进 fbx 文件中，这样最后导出的就只有一个 fbx 文件了。
- Limit to: Selected Objects，表示只导出选中的对象，而这时我已经选中了荧的模型，不然可能连骨架（可是是骨架吧）一并导出。

![blender_491gMBBDXV](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-c6f7aa2766f14a18cf662b874568f916-blender_491gMBBDXV.webp)

![explorer_W176hyUmnE](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-c61a70b92764598c829b9feac5e8f623-explorer_W176hyUmnE.webp)

8、之后就可以将 fbx 格式的荧的模型导入到 Unity 中了。不过这时还会出现因为材质的透明度而导致的黑色色块的原因。

![Unity_8qRXoFnKiy](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-bf6531e43de1e301889d888733316f22-Unity_8qRXoFnKiy.webp)

9、这时我们就需要修改材质球了，因为默认的材质球是不允许修改的，所以我们直接拷贝出来一个，并将其 **Rendering Mode** 修改为 **Cutout**，再将这个材质球应用到模型上即可。

ps：网上找到时候说需要将这个模式改为 Transparent ，但实际试下来感觉不对，之后无意间又试了 Cutout ，发现这个的效果才对。至于为什么要选这个，现阶段还是不知道，先把这个【问题】记录下，等 Unity 学完再看。

![Unity_ia0kUq2Qm8](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/11/10-c8e0bf68376ae6055b6ca5eda1b91933-Unity_ia0kUq2Qm8.webp)

> 20241111

### 09 没有资源？商城对你说NO

​	本节介绍了 Unity 的[资源商店](https://assetstore.unity.com/zh-CN)，以及资源下载，资源导入，资源管理相关的内容。

### 10 有山有路有悬崖？来创建个地形吧

​	本节介绍了地形对象，包含创建地形模型，对地形进行扩展，编辑（抬高、降低、山洞）等操作。

​	另外在场景绘制中，其坐标系，最小的单位1，可能表示1m。



## 学习后



