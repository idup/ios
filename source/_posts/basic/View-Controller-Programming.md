title: 控制器
date: 2015-06-01 17:31:45
category: IOS基础
tags:
---


视图控制器是应用的核心，主要负责：

* 视图管理
* 交互处理
* 数据传送
* 界面切换


### 视图管理

控制器最重要的角色就是负责视图（层次）的管理。每个控制器管理一个视图（及其子视图），当你希望把某个视图显示出来时，应该将此视图对应的控制器作为应用窗口的根控制器（rootViewController），该视图控制器会自动将视图添加到窗口中并显示在屏幕上，但永远不要尝试通过将视图赋予窗口对象的方法去显示其内容。视图控制器会在必要的时候加载并视图对象并显示其内容，同样，它会在合适的条件下自动释放视图（因此，视图控制器在应用中还起到管理资源的核心作用）

{% image /images/controller_load_view.png 500 "视图加载" %}

这一过程可使用编程方式完成。
```swift
func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObjects]?) -> Bool {
	self.window = UIWindow(frame:UIScreen.mainScreen().bounds)
	self.window!.rootViewController = ViewController()
	self.window!.makeKeyAndVisible()
	return true
}
```
每个视图控制器有（且仅有）一个根视图对象引用，可通过其访问到这个视图对象的所有子视图对象。一般使用[Outlet](https://developer.apple.com/library/ios/documentation/General/Conceptual/Devpedia-CocoaApp/Outlet.html)保存对视图对象的引用。我们可以在Interface Builder中创建Outlet

{% image /images/ib_outlet.png  "使用IB创建Outlet" %}


### 交互处理

除了管理视图加载，控制器还负责处理视图中产生的事件。当视图中某个按钮被按动，视图对象会获取该事件并报送给某个相关联的委托对象（delegte）或目标对象（target），一般而言，这个对象就是某个视图控制器对象。视图本身并不知晓这个事件将会引发的结果，按钮按动的含义和相应的反应是调用该视图控制器的某个方法（IBAction）。在获得这个事件发生的通知后，控制器可以执行更新数据或改变视图属性等操作，甚至将另一个视图控制器对应的视图内容展示在屏幕上。

{% image /images/ib_outlet.png  "使用IB关联事件到IBAction" %}

### 数据传送

视图控制器一般还需管理应用数据到视图的传递过程。这一过程一般为

1. 交互事件触发控制器方法调用
2. 方法执行过程中从数据对象获得数据
3. 再通过视图对象引用（Outlet）操纵视图内容

{% image /images/controller_data_transfer.png 300 "数据传送" %}

### 多控制器（界面）设计

iOS设备是移动设备，屏幕空间非常有限（哪怕是iPad pro），应用一般会有比较丰富的信息需要显示，但屏幕不能一次性显示所有内容，因此在用户与应用交互开始时应用仅会显示部分内容，并在以后过程中不断显示或隐藏其他内容，在此过程中视图控制器提供设施实现这一内容显示／隐藏的协同过程。通过不同控制器和对应的视图对应用进行分割，整个应用的用户界面被以较小的单位进行管理。如下图所示，每个视图由一个控制器管理，视图控制器相互通信实现这些分隔视图的切换过程，每个视图控制器操作应用的部分数据。

{% image /images/controller_multiple_views.png "分割的界面" %}

### 控制器分类
控制器可分为两类：内容视图控制器（Content View Controller）和容器视图控制器（Container View Controller）。

#### 内容视图控制器

内容视图控制器负责显示可视内容，包括将数据展示给用户，从用户处收集数据和执行特定操作等。例如下图所示的表视图控制器



{% image /images/controller_tableviewcontroller.png  300 "表视图控制器" %}


#### 容器视图控制器
容器视图控制器负责组织内容控制器，它包含其他视图控制器所管理的内容，被管理的视图控制器被显式地指定为容器视图控制器的子控制器。容器控制器可嵌套：它可作为其他容器控制器的子控制器，也可作为其他控制器的父控制器，通过这种形式控制器可形成层次结构（但跟视图层次不对应）。例如下图所示导航控制器

{% image /images/controller_navigationcontroller.png  400 "导航控制器" %}

以及iPad应用中常见的分栏视图控制器，如下图。


{% image /images/controller_splitviewcontroller.png  300 "分栏视图控制器" %}

### 控制器内容（视图）显示
有多种方式可以通过控制器显示其相应的视图

- 将某个控制器作为窗口对象的根视图控制器（上节已介绍）
- 将视图控制器作为加入一个容器控制器
- 让另一个控制器将其呈现（present）出来

#### 作为根视图控制器

{% image /images/controller_rootviewcontroller.png  300 "作为根视图控制器" %}


#### 使用容器控制器为根视图控制器

{% image /images/controller_container.png  400 "使用容器控制器为根视图控制器" %}


#### 由另一个控制器将其呈现（present）


{% image /images/controller_present.png  500 "由另一个控制器将其呈现" %}


#### 更复杂的情况

{% image /images/controller_complex.png  500 "复杂情况" %}


#### 用StoryBoard定义

StoryBoard中一个场景（scene）代表在屏幕上显示的由一个控制器管理的内容区域，即一个视图控制器即其所管理的视图层次。可在同一个Storyboard中的两个场景间建立一个关系，如下图所示。

{% image /images/controller_scenes.png  "场景关系" %}

其中的关系包括

- 包容关系（Containment）：两个场景的父子关系，前者一般对应一个容器控制器
- 延续关系（Segue）：从一个场景到另一个场景的转换（迁移），包括以下类型
 - Push segue：将目标视图控制器压入导航控制器所管理的控制器栈中(如下图所示)
 - Modal segue: 将目标视图控制器呈现出来
 - Popover segue: 将目标视图控制器在一个弹出窗口（popover）中显示出来
 - Custom segue: 允许你自行设计所需的展示目标视图控制器的切换过程

{% image /images/controller_segue.png  300 "Push Segue" %}



注：本部分内容主要参考文献为[View Controller Programming Guide for iOS](https://developer.apple.com/library/ios/featuredarticles/ViewControllerPGforiPhoneOS/Introduction/Introduction.html)。请对照[Start Developing iOS Apps (Swift) - Connect the UI to Code](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/DevelopiOSAppsSwift/Lesson3.html) 和[Start Developing iOS Apps (Swift) - Work with View Controllers](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/DevelopiOSAppsSwift/Lesson4.html)进行实践。
