title: Cassini
date: 2015-12-15 23:51:17
category: 应用示例
tags:
---

本教程将介绍如何在应用中使用并发编程技术。 相应代码位于[https://github.com/idup/Cassini](https://github.com/idup/Cassini)。

![](/picture/1-1.png)

### 1.新建项目

运行 Xcode ，选择 File->New->Project… (键盘快捷键是 Command + Shift + N )。 在新出现的窗口中,选择左侧iOS部分的 Application ,然后选择右边的 Single View Application (单窗口应用)模板,单击 Next 按钮。

在文本框 Product Name 中填入 Cassini , 在 Language 弹出式菜单中选择 Swift , 在 Devices 选择 iPhone 。确保标题为 Use Core Data 的选择框未被选中, 点击下一步按钮,单击创建按钮创建项目。

![](/picture/1-2.png)

### 2.拖拽界面

![](/picture/1-3.png)

![](/picture/1-4.png)

![](/picture/1-5.png)

![](/picture/1-6.png)

![](/picture/1-7.png)

![](/picture/1-8.png)

![](/picture/1-9.png)

![](/picture/2-0.png)

### 3.1 ImageViewController.swift

![](/picture/2-1.png)

TableViewController主要在点击Cell时，带上Cell.DetailTextLabel.text生成的NSURL对象，并赋值给Segue目标ViewController的属性。

### 3.2 ImageViewController.swift

![](/picture/2-2.png)

这里是多线程最直观的实现。
通过GCD的dispatch_async方法提交一个闭包到global_queue上。
通过NSData同步方法(contentsOfUrl: String)获取URL中的数据。
同步方法会Block住这个线程，在这个方法未返回时，不会向后执行。
获取完数据后，通过GCD相同的方法提交闭包到mian_queue上，设置图片数据并显示。
