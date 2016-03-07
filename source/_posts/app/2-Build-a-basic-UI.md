title: 二. 创建基本用户界面
date: 2015-12-08 11:11:31
category:  IOS应用开发
tags:
---



### 打开Storyboard

![打开Storyboard](/images/2-1.png)

### 添加文本框（Text Field）

从Object library中拖拽一个文本框到Storyboard的 scene中,重新设置文本框大小。

![添加文本框](/images/2-2.png)

### 设置文本占位符

打开工具框中的 Attributes inspector，找到Placeholder标签，在其中输入Enter meal name。

![设置占位符](/images/2-3.png)

### 设置文本框键盘

在Attributes inspector中找到Return Key标签，将其设置为Done,并在Auto-enable Return Key复选框上打上勾。

###  添加标签（Label）

从Object library中拖拽一个label到scene中，双击它，在其中输入Meal Name.

![添加标签](/images/2-4.png)

### 添加按钮（Button）

从Object library中拖拽一个button到scene中，双击它，在其中输入Set Default Label Text.

![添加按钮](/images/2-5.png)

### 自动布局

在按住shift的情况下点击label,button,和textfield.点击canvas底部的Stack按钮

![Stack](/images/2-6.png)

Xcode将会将所有UI元素包裹在一个stack view中

![Stack](/images/2-7.png)

在canvas的右下角，打开Pin菜单，可以修改界面的布局位置

![Pin](/images/2-8.png)

修改完成后

![Pin](/images/2-9.png)

需要调整text field的大小，在scene中选择text field,打开Pin菜单，将右边的box中输入0.

![Pin](/images/2-10.png)

在工具栏中选择Size inspector按钮,将标签Intrinsic Size的属性设置为Placeholder。

![size](/images/2-11.png)

最终的结果

![ui](/images/2-12.png)

运行模拟器

![simulator](/images/2-13.png)
