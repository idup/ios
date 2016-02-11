title: 控制器
date: 2015-06-01 17:31:45
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
