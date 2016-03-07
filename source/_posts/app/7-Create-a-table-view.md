title: 七. 创建表视图
date: 2015-12-03 11:59:11
category:  IOS应用开发
tags:
---
### 创建开放视图

目前，FoodTracker app只有一个通过view controller管理的视图，还需要创建meals的列表，IOS内置了表视图类UITableView来展示这种项目滑动列表

##### 在storyboard中添加一个表视图

在Object libray中找到Table View Controller对象，拖拽它把它放置在meal视图的左边，这时就有两个视图，一个用来用来添加meal，一个用来展示meal 列表

##### 将table view controller设置为初始视图

拖拽指向view Controller的箭头，将它指向table view controller

![](/images/7-1.png)

![](/images/7-2.png)

运行虚拟机

![](/images/7-3.png)

##### 配置table view

在 outline view中选择Table View，打开Size inspector,找到Row Height标签，设置为90

![](/images/7-4.png)

### 设计自定义的表单元

##### 创建UITableViewCell的子类

依次点击File > New > File ，选择ios下面的Source选项，选择 Cocoa Touch Class，点击next，Class中填入Meal,subclass of中选择UITableViewCell，然后一只默认设置到创建结束。

##### 为table view配置自定义单元

在outline中选择Table View Cell，打开它的Attributes inspector，找到 Identifier标签，输入MealTableViewCell。找到 Selection标签，选择None，打开 Size inspector，找到Row Height标签，输入90，打开Identity inspector，在Class标签中选择 MealTableViewCell.

##### 为自定义的table单元设计接口

依次点击 Editor > Canvas > Show Bounds Rectangles，

![](/images/7-5.png)

在Object library中选择Image View，拖拽它到表单元

![](/images/7-6.png)

打开image view的 Attributes inspector,选择 Image标签设置为defaultPhoto，在Object library中选择Label，拖拽它到表单元，挡在image view的右边

![](/images/7-7.png)

重新设置label的大小

![](/images/7-8.png)

从Object library中选择View ，拖拽到表单元，打开它的Size inspector,设置 Height和Width 分别为40，240，打开它的Identity inspector，设置 Class为RatingControl。打开Attributes inspector，找到 Interaction标签，撤销User Interaction Enabled

![](/images/7-9.png)

![](/images/7-10.png)


运行虚拟机

![](/images/7-11.png)

### 向项目中添加图片

打开 project navigator中的Assets.xcassets，添加一个文件夹，命名为Sample Images，在这个文件夹下添加New Image Set ，向其中添加图片。可以新建多个New Image Set。

![](/images/7-12.png)

### table单元和代码建立连接

##### 建立视图和MealTableViewCell.swift代码的连接

拖拽table 单元中的label到MealTableViewCell.swift的代码区，name 设置为nameLabel

![](/images/7-13.png)

![](/images/7-14.png)

拖拽table单元中的image view到 MealTableViewCell.swift代码区，位置放在刚刚建立的nameLabel属性下面，name设置为photoImageView

![](/images/7-15.png)

选择table view单元中的rating control，拖拽它到MealTableViewCell.swift代码区的photoImageView属性下。name设置为ratingControl

![](/images/7-16.png)

![](/images/7-17.png)


### 加载初始数据

##### 创建UITableViewController的子类

依次点击File > New > File，选择ios下的Source选项，选择Cocoa Touch Class，点击next,Class填入Meal,subclass of填入UITableViewController，确保Also create XIB file设置为unselected状态，点击创建。

##### 加载初始数据

在 MealTableViewController.swift代码区的class行下面添加如下代码

```
// MARK: Properties

var meals = [Meal]()
```

在viewDidLoad() 方法后面，添加如下方法
```
func loadSampleMeals() {
    let photo1 = UIImage(named: "meal1")!
    let meal1 = Meal(name: "Caprese Salad", photo: photo1, rating: 4)!

    let photo2 = UIImage(named: "meal2")!
    let meal2 = Meal(name: "Chicken and Potatoes", photo: photo2, rating: 5)!

    let photo3 = UIImage(named: "meal3")!
    let meal3 = Meal(name: "Pasta with Meatballs", photo: photo3, rating: 3)!

    meals += [meal1, meal2, meal3]
}
```

viewDidLoad()方法添加相关代码加载数据

```
override func viewDidLoad() {
    super.viewDidLoad()

    // Load the sample data.
    loadSampleMeals()
}

```

### 呈现数据

##### 呈现table view的部分

修改MealTableViewController.swift代码中numberOfSectionsInTableView(\_:)方法

```
override func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return meals.count
}
```

##### 配置并呈现table view中的单元

找到tableviewf方法将其改成如下形式

```
override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
    // Table view cells are reused and should be dequeued using a cell identifier.
    let cellIdentifier = "MealTableViewCell"
    let cell = tableView.dequeueReusableCellWithIdentifier(cellIdentifier, forIndexPath: indexPath) as! MealTableViewCell

    // Fetches the appropriate meal for the data source layout.
    let meal = meals[indexPath.row]

    cell.nameLabel.text = meal.name
    cell.photoImageView.image = meal.photo
    cell.ratingControl.rating = meal.rating

    return cell
}
```

##### 将table view controller scene指向MealTableViewController.swift

点击view controller的scene dock,打开Identity inspector，class标签选择MealTableViewController.

![](/images/7-18.png)

### 准备导航视图

##### 清理工程中无用的项目

选择Meal Name 标签，并删除它

![](/images/7-19.png)

![](/images/7-20.png)

打开ViewController.swift，找到 textFieldDidEndEditing(\_:)方法，删除方法中的如下代码
```
mealNameLabel.text = textField.text
```
删除ViewController.swift中的
```
@IBOutlet weak var mealNameLabel: UILabel!

```

##### 重命名ViewController.swift文件

点击ViewController.swift，重命名为MealViewController.swift，将代码区的类声明作如下修改

```
class MealViewController: UIViewController, UITextFieldDelegate, UIImagePickerControllerDelegate, UINavigationControllerDelegate {
```
在文件的上面部分将ViewController.swift 改为MealViewController.swift.

点击meal secen的scene dock，打开Identity inspector，将class改为MealViewController
