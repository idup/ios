title: iOS应用基础
date: 2015-08-01 17:28:32
tags:
---

一个iOS应用（App）是你所开发的代码和系统框架间交互过程的实现。系统框架提供应用运行所需的所有基础设施，你所写的代码提供了对基础设施个性化定制，实现了你所需要的用户交互界面和业务功能。

>本质上说，每个iOS应用都是一样的，你只是定义了一点特殊性。“我们不生产水，我们只是大自然的搬运工。”

## iOS应用架构


iOS应用总体架构遵循MVC架构模式。
{% image /images/model_view_controller.png 500 "MVC" %}


具体而言，大部分iOS应用的结构如下图所示。

{% image /images/core_objects.png 500 "iOS应用结构" %}


### UIApplication
UIApplication 。UIApplication任何时候都不应该被改变。
对象管理事件循环和高层的应用行为。它将应用的关键性状态变化和一些特定事件（例如收到一个推送的通知）报告给你所定义的“委托”对象（delegate）。UIApplication任何时候都不应该被改变。



### 主循环

应用的主循环负责处理所有用户相关的事件。 UIApplication对象负责在应用启动时为其创建主循环并以此处理事件。 

{% image /images/event_draw_cycle.png 500 "主循环中的事件处理" %}



主循环在应用主线程中执行，以确保用户相关事件严格按其发生先后的顺序得到处理。其中的事件包括

* 触摸（Touch）事件
* 甩动（Shake motion）事件
* 加速器、传感器事件
* 位置变化
* 界面重绘


### 应用委托（Delegate）

应用委托是应用的核心。该对象与UIApplication对象联合起来负责对应用的初始化过程、状态迁移过程和很多高层的应用事件进行处理。委托对象也是唯一一个每个应用都必须具有的对象，因此它一般还负责应用所需数据结构的初始化。


> Delegation is a simple and powerful pattern in which one object in a program acts on behalf of, or in coordination with, another object. The delegating object keeps a reference to the other object—the delegate—and at the appropriate time sends a message to it. The message informs the delegate of an event that the delegating object is about to handle or has just handled. The delegate may respond to the message by updating the appearance or state of itself or other objects in the application, and in some cases it can return a value that affects how an impending event is handled. The main value of delegation is that it allows you to easily customize the behavior of several objects in one central object.


{% image /images/delegation.png 500 "委托模式" %}


### 应用执行状态（生命周期）

{% image /images/high_level_flow.png 300 "应用状态转化" %}


### 文档和数据模型

数据模型对象被用以保存应用需要维护和管理的内容，例如

* 银行应用需要数据库存储相关的金融交易事务
* 画图应用需要保存用户所画的图像

### 视图

视图（View）是在一个特定矩形区域内可视内容，并可以响应在该区域内的用户交互事件。控件（Control）是特定类型的视图，例如按钮、输入框、开关等。UIKit 框架提供了很多标准的视图组件用以显示不同类型的内容，也可以通过继承UIView对象定制自己所需的视图。

### 视图控制器

视图控制器（View Controller）对象管理应用视图在屏幕上的显示。所有的视图控制器都是继承自UIViewController。视图控制器负责处理用户界面（视图）的加载、显示、旋转等系统行为。在UIKit和其他框架中也定义了很多额外的视图控制器用以实现一些标准的系统界面的管理，例如图片选取、导航和标签栏等。


### UIWindow
UIWindow 对象代表应用在屏幕上的现实窗口，负责协调视图在设备屏幕上的显示。一般而言每个应用拥有一个窗口并将窗口内的内容显示在设备主屏幕上，如果存在外部现实设备，应用也可以具有额外的窗口。除了用以显示内容外，窗口也负责协助UIApplication对象将系统事件传递到视图和视图控制器以便处理。


### 应用终止

应用必须随时准备被终止。可能的情况包括：

* 系统需要为用户启动的其他应用分配内存
* 应用存在不良行为或未能及时响应

一旦收到系统发出的终止通知，应用需要及时终止当前操作并保存需要保存的数据。

### 线程和并发

系统为应用运行创建一个线程（主线程），应用也可以创建额外线程已运行其他任务

* 视图、动画等相关操作必须在主线程运行（线程安全性）
* 图片操作、网络通信、文件存取、大量数据处理等操作必须用GCD或Operation对象方式实现并行
* 应用启动时，主线程内计算和操作应尽量减少，以便应用能更快速地准备好用户界面

## 参考文献

iOS应用编程指南（（App Programming Guide for iOS） <https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html>




