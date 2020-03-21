---
layout:     post
title:      Ubuntu To Go 与 Moblie Disk 的共赢手段
subtitle:   装有Linux系统的移动硬盘如何分出一份区域供Windows存储
date:       2020-03-22
author:     BabyXin
header-img: img/post/post-2020-3-21/post-bg-HHD.jpg
header-mask: 0.4
catalog: true
tags:
    - Ubuntu
    - 双系统
---

## 前言

作者最近在尝试把Ubuntu系统装在移动硬盘中。系统安装成功了，但是500G的硬盘装一个Ubuntu总是有些浪费。在网上也没有找到相关的教程，于是自己捣鼓做了一下。



## 第一步: 压缩卷

首先，将你的移动硬盘接入电脑。

在windows搜索栏中搜索“硬盘”，即可进入控制面板的`创建并格式化硬盘分区`功能。

插入移动硬盘，可以发现你的移动硬盘有若干个分区。

![](https://raw.githubusercontent.com/BabyXinORZ/IMG_CLOUD/master/data/post-body-disk.png)

可以选中你觉得太大的分区，右键压缩,弹出如下窗口。

![](https://raw.githubusercontent.com/BabyXinORZ/IMG_CLOUD/master/data/post-body-space.png)

输入你想要压缩的量（就是你想要拿来作为存储空间的量），点击压缩。压缩后，盘中会新增一部分未分配空间/可用空间，那就是我们要用来存储的空间


## 第二步：转换格式

右键未分配空间/可用空间，点击新建简单卷。输入你想要的存储空间大小，驱动器号按照默认即可（第二个和第三个都不能被识别为可存储介质）。

![](https://raw.githubusercontent.com/BabyXinORZ/IMG_CLOUD/master/data/post-body-select.png)

在下一步中，文件系统使用NTFS，分配单元大小为默认值，卷标为你想要命名的名字（之后可以重命名，所以不同担心）。

![](https://raw.githubusercontent.com/BabyXinORZ/IMG_CLOUD/master/data/post-body-format.png)

下一步后检查一下自己的配置，无误后点击完成即可。

## 第三步：测试

在Windows中，移动硬盘会在`此电脑`下显示。

在Ubuntu中，移动硬盘会在菜单栏和文件管理器中显示，可以自由访问。

另外，在Ubuntu系统中会显示一些Win10下看不见的文件。

![](https://raw.githubusercontent.com/BabyXinORZ/IMG_CLOUD/master/data/post-body-folder.png) 

估计这些文件**对windows中的分盘会有影响**，作者没有删除进行测试，也没有找到什么隐藏的方法。如果有知道的朋友欢迎在评论区留言。


## 结语

本文其实就是做了一个把EXT4文件系统转为了NTFS文件系统的工作，非常的简单。Ubuntu其实是可以自由访问Windows下的文件的，但是Windows就需要借助一些像`DiskInternals Linux Reader`，`Ext2Read`之类的软件。为了追求方便，当然是直接转为windows能直接浏览的NTFS文件系统会更好啦！