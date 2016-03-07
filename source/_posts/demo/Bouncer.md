title: Bouncer
date: 2015-12-15 23:51:29
category: 应用示例
tags:
---

本教程将介绍如何在应用中使用手势和传感器技术。 相应代码位于[https://github.com/idup/Bouncer](https://github.com/idup/Bouncer)。

![](/picture/3-1.png)

### 1.新建项目

运行Xcode，选择File->New->Project...(键盘快捷键是Command + Shift + N)。在新出现的窗口中，选择左侧iOS部分的Application，然后选择右边的Single View Application（单窗口应用）模板，单击Next按钮。
在文本框Product Name中填入Bouncer, 在Language弹出式菜单中选择Swift，在Devices弹出式菜单中选择iPhone。确保标题为Use Core Data的选择框未被选中，点击下一步按钮,单击创建按钮创建项目。

![](/picture/3-2.png)

###  2.Core Motion

Core Motion对CMMotionManager,CMAccelerometerData,CMDeviceMotion, CMGyroData进行了很好的封装,可以让开发者进行方便的管理。
￼
CMMotionManager可以访问所有从iOS设备上获取的Core Motion数据。主要方式 分为pull和push两种,pull需要手动向manager索要数据,即最近一次的采样数据, 而push方式则是自动在每一个采样数据到来的时候执行闭包里面的函数进行处理。

![](/picture/3-3.png)


#### 2.1加速计原理

iPhone的加速度计有三个轴,分别是x轴、y轴、z轴,如上图所示。这是一个三 维立体空间,可以捕获用户每一个角度的操作。通过这三个轴可以计算iPhone倾斜的 角度,从而计算出加速度。

(1)对于iphone手机来说,画面上下为y轴,左右为z轴,贯穿屏幕为z轴。

(2)向上,向右,手机的前面分别是各轴的正方向。

#### 2.2加速计使用步骤

(1)实例化CMMotionManager类

(2)向CMMotionManager的accelerometerUpdateInterval属性中设置通知间隔 时间值。

(3)使用NSOperationQueue.currentQueue()建立一个监听队列。

(4)使用startAccelerometerUpdatesToQueue方法更新监听队列,并设置回调 函数用于接受加速度通知。在回调函数中使用accelerometerData.acceleration相关 属性可以获取x、y、z各个方向的加速度。

#### 2.3频率设置建议

accelerometerUpdateInterval表示通知频率,表示间隔多少秒通知一次。 iPhone开发文档中推荐使用的通知间隔如下:

(1)检测设备朝向:1/10 ~ 1/20

(2)在游戏中需要实时使用加速传感器时:1/30 ~ 1/60

(3)检测敲击设备或者剧烈摇动设备的情况下:1/70 ~ 1/100

### 3.code

相关代码请参考Demo

#### 3.1AppDelegate.swift

打开AppDelegate.swift代码窗口,删除class内代码,由于APP中所有用 CoreMotion的对象都需要使用同一个实例,所以需要在AppDelegate中新建Manager, 代码如下。

```
struct Motion {
        static let Manager = CMMotionManager()
    }
```

当然,首先应该导入CoreMotion库。

```
import CoreMotion
```

#### 3.2BouncerBehavior.

在BouncerBehavior.swift中,我们封装了Bouncer需要用到的 UIDynamicBehavior。我们定义了gravity,collider,blockBehavior三个成员变 量,并对后两者进行了lazy init。

之所以使用lazy init,原因有二:

一来构造collider的时候有的东西不能使用,二来构造的时候需要设置属性。

 blockBehavior可以改变动力元素的一些属性,如修改allowsRotation属性可以
设置元素是否可以旋转,修改elasticity属性决定碰撞是否为弹性碰撞,能量损耗是 多少等等。具体可以参见apple官网的开发者指南。

```
let gravity = UIGravityBehavior()
    lazy var collider: UICollisionBehavior = {
        let lazilyCreatedCollider =
UICollisionBehavior()
lazilyCreatedCollider.translatesReferenceBoundsIntoB
oundary = true
        return lazilyCreatedCollider
    }()
    lazy var blockBehavior: UIDynamicItemBehavior =
{
        let lazilyCreatedBlockBehavior =
UIDynamicItemBehavior()
        lazilyCreatedBlockBehavior.allowsRotation =
        lazilyCreatedBlockBehavior.elasticity = 0.85
        lazilyCreatedBlockBehavior.friction = 0
        lazilyCreatedBlockBehavior.resistance = 0
        return lazilyCreatedBlockBehavior
}()
在重写的init方法中,我们将gravity,collider,blockBehavior加入到当前 行为规则中。同时又添加了addBlock和removeBlock两个封装好的方法,用来添加和 移除遵循行为的对象。
true
override init() {
        super.init()
        addChildBehavior(gravity)
        addChildBehavior(collider)
        addChildBehavior(blockBehavior)
    }
func addBlock(block: UIView) {
dynamicAnimator?.referenceView?.addSubview(block)
        gravity.addItem(block)
        collider.addItem(block)
        blockBehavior.addItem(block)
    }
func removeBlock(block: UIView) {
        gravity.removeItem(block)
        collider.removeItem(block)
        blockBehavior.removeItem(block)
        block.removeFromSuperview()
}
```
#### 3.3ViewController.swift

在ViewController.swift中我们做如下三件事:
首先,建立建立Animation Behavior,并且绑定当前view为UIDynamicAnimator的referenceView。

```
let bouncer = BouncerBehavior()
    lazy var animator: UIDynamicAnimator =
{ UIDynamicAnimator(referenceView: self.view) }()
```

其次,在View Controller的生命周期中控制数据采集的开始和结束,并向其中添加对象。

```
override func viewDidLoad() {
        super.viewDidLoad()
        animator.addBehavior(bouncer)
    }
override func viewDidAppear(animated: Bool) {
        super.viewDidAppear(animated)
        if redBlock == nil {
            redBlock = addBlock()
            redBlock?.backgroundColor =
UIColor.redColor()
            bouncer.addBlock(redBlock!)
}
        let motionManager =
AppDelegate.Motion.Manager
        if motionManager.accelerometerAvailable
{ motionManager.startAccelerometerUpdatesToQueue(NSO
perationQueue.mainQueue()) { (data, error) -> Void
in
self.bouncer.gravity.gravityDirection = CGVector(dx:
data!.acceleration.x, dy: -data!.acceleration.y)
} }
}
override func viewWillDisappear(animated: Bool) {
        super.viewWillDisappear(animated)
AppDelegate.Motion.Manager.stopAccelerometerUpdates(
)
}
```
最后,还要封装addBlock方法,添加视图。

```
var redBlock: UIView?
    func addBlock() -> UIView {
        let block = UIView(frame: CGRect(origin:
CGPoint.zero, size: Constants.BlockSize))
        block.center = CGPoint(x: view.bounds.midX,
y: view.bounds.midY)
        view.addSubview(block)
        return block
    }
struct Constants {
        static let BlockSize = CGSize(width: 40,
height: 40) }
```

### 4.运行项目

由于Xcode7之后支持直接进行真机调试而不需 要开发者账号,因此我们将设备与Mac连接后, 在模拟器列表中选择我们的设备,然后点击运 行即可(快捷键 Command + R)。

![](p/icture/3-4.png)
