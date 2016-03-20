title: 八. 实现导航
date: 2015-12-02 11:59:23
category:  iOS应用示例
tags:
---

### 添加一个向前导航

现在需要添加meal list到meal scene的导航

##### 增加一个navigation controller指向meal list scene

打开storyboard，点击scene dock来选择table view controller,保持选择状态依次点击Editor > Embed In > Navigation Controller.

![](/images/8-1.png)

### 为视图添加导航栏

##### 为meal list配置导航栏

双击meal list scene的 navigation bar，输入Your meals

![](/images/8-2.png)

![](/images/8-3.png)

从Object library中选择Bar Button Item，拖放到meal scene的右上角

![](/images/8-4.png)

选择它的 Attributes inspector,从菜单中选择Add，这个btton就会变成增加按钮

![](/images/8-5.png)

运行虚拟机

![](/images/8-6.png)

##### 在meal scene中添加add按钮

选择add button(+)，按住control键并拖入meal scene中，出现一个Action Segue菜单，选择show选项

![](/images/8-7.png)

![](/images/8-8.png)

![](/images/8-9.png)

运行app,点击add 按钮，并导航至meal scene

##### 改变segue style

选择segue，在它的Attributes inspector中选择 Present Modally，在Identifier标签上选择AddItem

##### 给meal scene增加一个navigation controller

选择meal scene，依次点击Editor > Embed In > Navigation Controller.

##### 在meal scene中配置导航栏

双击navigation bar，输入New Meal保存，从 Object library中拖一个 Bar Button Item放在meal scene的导航栏上，在Attributes inspector中选择 Cancel

![](/images/8-10.png)

拖拽另一个Bar Button Item放在meal scene的导航栏上，在Attributes inspector上选择save

![](/images/8-11.png)

运行app

![](/images/8-12.png)

### 最后确定自动布局的界面

##### 更新stack view的布局

点击meal scene中的蔚蓝色区域以选择stack view，在canvas的右下角，打开Resolve Auto Layout Issues菜单，选择Update Constraints

![](/images/8-13.png)

![](/images/8-14.png)


### 在Meal List中存储新的Meals

##### 在MealViewController中增加一个Meal属性

打开MealViewController.swift.在ratingControl下增加如下代码

```
/*
This value is either passed by `MealTableViewController` in `prepareForSegue(_:sender:)`
or constructed as part of adding a new meal.
*/
var meal: Meal?
```

##### 建立save按钮与MealViewController代码的连接

打开storyboard，将save 按钮拖至MealViewController.swift代码的ratingControl属性下面，name设置为saveButton

![](/images/8-15.png)

![](/images/8-16.png)

### 创建一个松开 Segue

##### 在MealViewController中实现prepareForSegue(\_:sender:) 方法

打开MealViewController.swift，在// MARK: Actions上面，添加

```
// MARK: Navigation
// This method lets you configure a view controller before it's presented.
override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?) {
    if saveButton === sender {
        let name = nameTextField.text ?? ""
        let photo = photoImageView.image
        let rating = ratingControl.rating

        // Set the meal to be passed to MealTableViewController after the unwind segue.
        meal = Meal(name: name, photo: photo, rating: rating)
    }
}
```

##### 给MealTableViewController添加动作方法

打开MealTableViewController.swift.在最后一个 } 前添加如下代码

```
@IBAction func unwindToMealList(sender: UIStoryboardSegue) {
    if let sourceViewController = sender.sourceViewController as? MealViewController, meal = sourceViewController.meal {
        // Add a new meal.
        let newIndexPath = NSIndexPath(forRow: meals.count, inSection: 0)
        meals.append(meal)
        tableView.insertRowsAtIndexPaths([newIndexPath], withRowAnimation: .Bottom)
    }
}
```

##### 将save按钮与unwindToMealList 方法建立连接

打开storyboard，按住control键拖拽Save 按钮到meal scene上面的 Exit 按钮，在出现的菜单中选择unwindToMealList:

![](/images/8-17.png)

![](/images/8-18.png)

###  当用户没有输入名字时不能存储

##### 没有名字，不能使用save按钮

在MealViewController.swift中找到
```
// MARK: UITextFieldDelegate
```
在这个部分添加另一个方法
```
func textFieldDidBeginEditing(textField: UITextField) {
    // Disable the Save button while editing.
    saveButton.enabled = false
}
```
在textFieldDidBeginEditing(\_:)方法之后添加另一个方法
```
func checkValidMealName() {
    // Disable the Save button if the text field is empty.
    let text = nameTextField.text ?? ""
    saveButton.enabled = !text.isEmpty
}
```
找到textFieldDidEndEditing(\_:)方法，向其中添加
```
checkValidMealName()
navigationItem.title = textField.text
```
找到viewDidLoad() 方法，向其中添加

```
// Enable the Save button only if the text field has a valid Meal name.
checkValidMealName()
```
### 取消新增的meal

##### 创建并是吸纳一个取消动作方法

选择Cancel button，将其拖入MealViewController.swift代码区域的// MARK: Navigation下面，name 设置为cancel，type设置为UIBarButtonItem.

![](/images/8-19.png)

![](/images/8-20.png)

在cancel(\_:)中添加
```
dismissViewControllerAnimated(true, completion: nil)
```
