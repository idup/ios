title: 视图
date: 2015-07-01 17:31:34
tags:
---

窗口和视图将应用的可视界面展示在屏幕上。其中屏幕是iOS设备所具有的显示装置，一般而言每个iOS设备具有至少一个（主）屏幕；窗口提供了一个基本的视图的容器，窗口本身并不具有可视内容，一般而言每个应用具有一个窗口；视图占据窗口的部分区域用以显示交互界面内容；一般而言每个应用至少具有一个视图用以展示其交互界面。

### 窗口

每个iOS应用都需要至少一个窗口。窗口用以显示应用的可视界面内容，窗口对象是UIWindow类型的一个实例，窗口负责将系统中发生的touch事件传递到你的视图和其他应用对象以供处理，如果发生设备朝向（orientation）变化事件，窗口对象和应用的视图控制器对象对进行协作。

如果使用StoryBoard，则系统会自动创建和管理窗口对象，或者可通过编程方式手工创建和管理窗口。

```swift
func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject AnyObject]?) -> Bool {
	self.window = UIWindow(frame:UIScreen.mainScreen().bounds)
	return true
}
```

### 视图

应用中所需要显示的可视内容一般通过视图对象定义。每个视图对象都是 UIView 的子类。一个视图对象定义了在一个矩形区域范围内的可视内容和这些内容在屏幕上的绘制过程，并负责处理该矩形区域内发生的用户交互（触碰）事件。

系统中UIKit和其他一些框架提供了预先定义好的视图和控件以供你的应用所使用，预定义的视图和控件包括简单的按钮、文本标签和复杂的表格视图（Table View）、选取器（Picker View）、滚动视图（Scroll View）等。如果预定义的这些视图并不能满足你的要求，也可以自己定义个性化视图和控件，包括对视图绘制和事件处理的定制。

UIKit中定义的UIView的子类（系统预定义的视图和控件）详见 [UIKit User Interface Catalog](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/UIKitUICatalog/index.html)


一个视图可以充当另一个视图的父视图，并管理其位置放置和大小调整等，这些相互间存在父子关系的视图形成一个视图层次。

{% image /images/view_hierarchy.png 500 "视图层次" %}

视图可以使用Interface Builder来创建。如下图所示。

{% image /images/ib_view.png 500 "视图创建" %}

也可以在Interface Builder中创建视图层次。如下图所示。

{% image /images/ib_view_hierarchy.png 500 "视图层次创建" %}


其中工具栏的Inspector上可对视图的诸多属性进行设置，包括：
* File inspector：设置视图对应的Storyboard或xib文件的属性，包括名字，自动布局等
* Quick Help inspector：显示当前选择项的文档
* Identity inspector：设置当前选择项的元信息，包括类型、标签等
* Attributes inspector：设置当前选择对象的各类属性
* Size inspector：设置当前选择项的尺寸和位置等
* Connections inspector：outlet、action和storyboard segues的设置

详见 [Interface Builder Help](https://developer.apple.com/library/ios/recipes/xcode_help-interface_builder/)

也可以对视图进行自动布局，详见 [Auto Layout Guide](https://developer.apple.com/library/prerelease/ios/documentation/UserExperience/Conceptual/AutolayoutPG/)

当然，我们也通过编写代码创建视图。

```swift
override func loadView(){
	super.loadView()
	let myView = UIView(frame:CGRect(x: 0, y: 0, width:100, height: 100))
	myView.backgroundColor = UIColor.greenColor()
	self.view = myView
}
```

运行结果如下图。

{% image /images/coding_view.png 300 "视图编程" %}

注意：以上视图之所以全屏是因为该视图的视图控制器是当前应用Windows对象的根视图控制器，详见[UIViewController Class Reference](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIViewController_Class/index.html)
>  … If a view controller is owned by a window object, it acts as the window’s root view controller. The view controller’s root view is added as a subview of the window and resized to fill the window. If the view controller is owned by another view controller, then the parent view controller determines when and how the child view controller’s contents are displayed. ..

同样，也可以通过编写代码创建视图层次，例如：

```swift
override func loadView(){
	super.loadView()

	let rectView = UIView(frame: CGRect(x: 0, y: 0, width: 200, height: 600))
	rectView.backgroundColor = UIColor.redColor()

	let label = UILabel(frame: CGRect(x: 0, y: 0, width: 100, height: 200))
	label.text = "This is a label"
	label.backgroundColor = UIColor.blueColor()

	rectView.addSubview(label)
	self.view.addSubview(rectView)

	self.view.backgroundColor = UIColor.greenColor()
}
```

运行结果如下图。

{% image /images/coding_view_hierarchy.png 300 "视图编程" %}


视图（层次）通过以下代码显示在设备屏幕上。

```swift
func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObjects]?) -> Bool {
	self.window = UIWindow(frame:UIScreen.mainScreen().bounds)
	self.window!.rootViewController = ViewController()
	self.window~.makeKeyAndVisible()
	return true
}
```

其原理如下图所示（其中涉及视图控制器概念）

{% image /images/view_display.png 500 "视图显示" %}


还可以通过编程定义自己的视图类型，例如：

```swift
import UIKit

class MyView: UIView {
	
	override func drawRect ( rect: CGRect ){
		let context = UIGraphicsGetCurrentContext()
		let myFrame = self.bounds
		CGContextSetLineWidth(context, 10)
		CGRectInset(myFrame, 5, 5)
		UIColor.blueColor().set()
		UIRectFrame(myFrame)
	}
}

override func loadView() {
	super.loadView()
	let myView = MyView(frame: CGRect(x: 0, y: 0, width: 200, height: 300))
	self.view.addSubview(myView)
	self.view.backgroundColor = UIColor.greenColor()
}
```

将得到以下结果：
{% image /images/custom_view.png 300 "自定义视图" %}


一般而言，视图总是和Core Animation 层框架所提供功能协作完成视图的渲染和动画过程。

{% image /images/view_calayer.jpg 500 "视图与动画" %}

基于Core Animation的支持，实现视图的变形、缩放、旋转等。例如

```swift
override func loadView() {
	super.loadView()

	let rectView = UIView(frame: CGRect(x: 0, y: 0, width:200, height: 600))
	rectView.backgroundColor = UIColor.redColor()
	self.view.backgroundColor = UIColor.greenColor()
	self.view.addSubview(rectView)

	let xform = CGAffineTransformMakeRotation(CGFloat(M_PI)/4)

	rectView.transform = xform
}
```

将得到以下运行结果。

{% image /images/view_transform.png 300 "视图变换" %}

具体可参考[Quartz 2D Programming Guide](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html)


这一变换过程还可以通过动画形式展示，只需要将上述代码稍作改变：
```swift
override func loadView() {
	super.loadView()

	let rectView = UIView(frame: CGRect(x: 0, y: 0, width:200, height: 600))
	rectView.backgroundColor = UIColor.redColor()
	self.view.backgroundColor = UIColor.greenColor()
	self.view.addSubview(rectView)

	UIView.beginAnimatins("rotateView", context: nil)
	UIView.setAnimationDuration(3)

	let xform = CGAffineTransformMakeRotation(CGFloat(M_PI)/4)
	rectView.transform = xform

	UIView.commitAnimations()
}
```

或者写为使用“闭包”的代码形式：

```swift
override func loadView() {
	super.loadView()

	let rectView = UIView(frame: CGRect(x: 0, y: 0, width:200, height: 600))
	rectView.backgroundColor = UIColor.redColor()
	self.view.backgroundColor = UIColor.greenColor()
	self.view.addSubview(rectView)

	let xform = CGAffineTransformMakeRotation(CGFloat(M_PI)/4)

	UIView.animateWithDuration(3, animations: { () -> Void in
		rectView.transform = xform
		}, completion: { (Bool) -> Void in
			print("finished")
	})

}
```

关于闭包（Closures）可具体参考<https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Closures.html>


注：本部分内容主要参考文献为[View Programming Guide for iOS](https://developer.apple.com/library/ios/documentation/WindowsViews/Conceptual/ViewPG_iPhoneOS/Introduction/Introduction.html)。请对照[Start Developing iOS Apps (Swift) - Build a Basic UI](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/DevelopiOSAppsSwift/Lesson2.htm) 进行实践。


