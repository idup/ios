title: Camera
date: 2015-12-16 11:41:29
category: 应用示例
tags:
---

本教程主要介绍如何在应用中使用摄像头技术。 相应代码位于 [https://github.com/idup/Camera](https://github.com/idup/Camera)

#### 1.新建项目

运行 Xcode ,选择 File->New->Project... (键盘快捷键是 Command + Shift + N )。 在新出现的窗又中,选择左 侧iOS部分的 Application ,然后选择右 边的 Single View Application (单窗又应用)模板,单击 Next 按钮。 在文本框 Product Name 中填入 Cassini , 在 Language 弹出式菜单中选择 Swift , 在 Devices 选择 iPhone 。确保标 题为 Use Core Data 的选择框未 被选中, 点击下一步按钮,单击创建按钮创建项目。

![](/picture/5-1.png)

#### 2.拖拽界面并采用autolayout布局
￼
![](/picture/5-2.png)

![](/picture/5-3.png)

![](/picture/5-4.png)

##### 3.1实现action sheet并初始化一个UIImagepicker

在swift中,action sheet 升级为 view controller,所以在使用的时候要先
init一个action sheet 然后添加相对应的action。
UIImagepicker 是对camera最简单的操作的API,我们可以相对容易地调 用UIImagepicker来实现平实对image操作的大部分功能,但是,当你有 更高级的自定义需求时,需要采用AVFoundation来更高级地自定义对多 媒体设备的操作。(详情见教程)

![](/picture/5-5.png)

##### 3.2 实现UIImagepicker delegate

继承 UIImagepicker delegate,实现它的delegate函数,就能够拿到 camera或者photo library中用户选择的图片或者视频。

![](/picture/5-6.png)
