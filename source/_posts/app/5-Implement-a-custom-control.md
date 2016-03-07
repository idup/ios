title: 五. 实现自定义控件
date: 2015-12-05 11:58:40
category:  IOS应用开发
tags:
---

### 创建自定义视图

点击File > New > File ，选择ios下的source选项，选择Cocoa Touch Class，点击next，Class设置为RatingControl，“Subclass of”选择UIView,Language选择Swift

![](/images/5-1.png)

在RatingControl.swift代码区的class里添加代码

```
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)
}
```

### 显示自定义视图

从Object library中拖拽一个View,将其放置在image view下面，打开它的Size inspector，Intrinsic Size标签设置为Placeholder，宽和高分别设置为44和240,打开它的 Identity inspector，class标签选择RatingControl.

### 向视图添加button按钮

在RatingControl.swift代码区添加如下代码，用于创建一个红色按钮
```
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)

    let button = UIButton(frame: CGRect(x: 0, y: 0, width: 44, height: 44))
    button.backgroundColor = UIColor.redColor()
    addSubview(button)
}
```

调整红色按钮的布局，重写intrinsicContentSize方法

```
override func intrinsicContentSize() -> CGSize {
    return CGSize(width: 240, height: 44)
}
```

运行模拟器

![](/images/5-2.png)

为了向button按钮添加动作，在 RatingControl.swift代码区最后一个 } 前添加如下代码

```
// MARK: Button Action
func ratingButtonTapped(button: UIButton) {
    print("Button pressed 👍")
```
修改init?(coder:)函数如下

```
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)

    let button = UIButton(frame: CGRect(x: 0, y: 0, width: 44, height: 44))
    button.backgroundColor = UIColor.redColor()
    button.addTarget(self, action: "ratingButtonTapped:", forControlEvents: .TouchDown)
    addSubview(button)
}
```


定义属性和5个button，重写layoutSubviews()方法

```
super.init(coder: aDecoder)

   for _ in 0..<5 {
       let button = UIButton(frame: CGRect(x: 0, y: 0, width: 44, height: 44))
       button.backgroundColor = UIColor.redColor()
       button.addTarget(self, action: "ratingButtonTapped:", forControlEvents: .TouchDown)
       ratingButtons += [button]
       addSubview(button)
   }
   override func layoutSubviews() {
       var buttonFrame = CGRect(x: 0, y: 0, width: 44, height: 44)

       // Offset each button's origin by the length of the button plus spacing.
       for (index, button) in ratingButtons.enumerate() {
           buttonFrame.origin.x = CGFloat(index * (44 + 5))
           button.frame = buttonFrame
       }
   }

```
### 为button大小声明约束,相应代码修改如下

```
override func layoutSubviews() {
    // Set the button's width and height to a square the size of the frame's height.
    let buttonSize = Int(frame.size.height)
    var buttonFrame = CGRect(x: 0, y: 0, width: buttonSize, height: buttonSize)

    // Offset each button's origin by the length of the button plus some spacing.
    for (index, button) in ratingButtons.enumerate() {
        buttonFrame.origin.x = CGFloat(index * (buttonSize + 5))
        button.frame = buttonFrame
    }
}
```
```
override func intrinsicContentSize() -> CGSize {
    let buttonSize = Int(frame.size.height)
    let width = (buttonSize + spacing) * stars

    return CGSize(width: width, height: buttonSize)
}
```
```
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)

    for _ in 0..<5 {
        let button = UIButton()
        button.backgroundColor = UIColor.redColor()
        button.addTarget(self, action: "ratingButtonTapped:", forControlEvents: .TouchDown)
        ratingButtons += [button]
        addSubview(button)
    }
}
```
### 向Buttons中添加star图片

在project navigator中选择Assets.xcassets,点击(+)按钮并创建一个文件夹，将文件夹命名Rating Images。在这个文件夹下创建两个Image Set，分别命名为emptyStar， filledStar，并将图片拖拽到相应位置

![](/images/5-3.png)

为buttons设置成星星图片，修改RatingControl.swift中代码

```
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)

    let emptyStarImage = UIImage(named: "emptyStar")
    let filledStarImage = UIImage(named: "filledStar")

    for _ in 0..<5 {
        let button = UIButton()

        button.setImage(emptyStarImage, forState: .Normal)
        button.setImage(filledStarImage, forState: .Selected)
        button.setImage(filledStarImage, forState: [.Highlighted, .Selected])

        button.adjustsImageWhenHighlighted = false

        button.addTarget(self, action: "ratingButtonTapped:", forControlEvents: .TouchDown)
        ratingButtons += [button]
        addSubview(button)
    }
}
```
运行模拟器

![](/images/5-3.png)

### 实现Button动作

用户需要点击星星图标来作出选择，需要重新设计rratingButtonTapped(\_:)方法

在RatingControl.swift代码区域添加updateButtonSelectionStates()方法
```
func updateButtonSelectionStates() {
    for (index, button) in ratingButtons.enumerate() {
        // If the index of a button is less than the rating, that button shouldn't be selected.
        button.selected = index < rating
    }
}
```
在ratingButtonTapped(\_:)方法和layoutSubviews()中分别调用这个方法

```
func ratingButtonTapped(button: UIButton) {
    rating = ratingButtons.indexOf(button)! + 1

    updateButtonSelectionStates()
}
```
```
override func layoutSubviews() {
    // Set the button's width and height to a square the size of the frame's height.
    let buttonSize = Int(frame.size.height)
    var buttonFrame = CGRect(x: 0, y: 0, width: buttonSize, height: buttonSize)

    // Offset each button's origin by the length of the button plus some spacing.
    for (index, button) in ratingButtons.enumerate() {
        buttonFrame.origin.x = CGFloat(index * (buttonSize + 5))
        button.frame = buttonFrame
    }
    updateButtonSelectionStates()
}
```
在// MARK: Properties区域下，更新rating属性

```
var rating = 0 {
didSet {
    setNeedsLayout()
}
}

```
运行模拟器

![](/images/5-5.png)

### 增加Spacing和Number属性

在// MARK: Properties下增加两个属性,

```
var spacing = 5
var stars = 5
```

### 将比率控制和视图控制器建立连接

将canvas中的rating control拖拽至 ViewController.swift中photoImageView 属性下

![](/images/5-6.png)

设置如图

![](/images/5-7.png)

### 清理工程项目

现在快要完成app的设计了，但是现在需要对之前的工作做一个清理，因为app实现了更高级的功能，而之前的功能我们需要删除一些。

选择Storyboard 中的Set Default Label Text 按钮，按下 Delete键去删除它

点击outline目录下的Stack View对象，打开Attributes inspector.找到Alignment标签，将其设置为Center，stack view中的元素就会水平居中

![](/images/5-8.png)

打开ViewController.swift，删除setDefaultLabelText(\_:)方法

运行模拟器

![](/images/5-9.png)
