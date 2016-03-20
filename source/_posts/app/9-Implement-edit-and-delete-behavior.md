title: 九. 实现编辑和删除操作
date: 2015-12-01 11:59:42
category:  iOS应用示例
tags:
---

### 允许编辑已经存在的Meals

##### 配置table view单元

打开Main.storyboard，选择table view cell，按住control并把它拖到meal scene中，在出现的Selection Segue中选择show选项

![](/images/9-1.png)

![](/images/9-2.png)

向下拖拽在meal list和meal scene之间的navigation controller，到出现新的segue结束

![](/images/9-3.png)

选择最新添加的segue，在它的 Attributes inspector中的Identifier标签中输入ShowDetail

##### 确认哪一个segue 在发生

打开MealTableViewController.swift，找到prepareForSegue(\_:sender:)方法，并修改为如下
```
// MARK: - Navigation

// In a storyboard-based application, you will often want to do a little preparation before navigation
override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?) {
    if segue.identifier == "ShowDetail" {
        let mealDetailViewController = segue.destinationViewController as! MealViewController

        // Get the cell that generated this segue.
        if let selectedMealCell = sender as? MealTableViewCell {
            let indexPath = tableView.indexPathForCell(selectedMealCell)!
            let selectedMeal = meals[indexPath.row]
            mealDetailViewController.meal = selectedMeal
        }
    }
    else if segue.identifier == "AddItem" {
        print("Adding new meal.")
    }
}
```

##### 更新viewDidLoad的实现

找到 MealViewController.swift的viewDidLoad()方法，修改内容如下
```
override func viewDidLoad() {
    super.viewDidLoad()

    // Handle the text field’s user input via delegate callbacks.
    nameTextField.delegate = self

    // Set up views if editing an existing Meal.
    if let meal = meal {
        navigationItem.title = meal.name
        nameTextField.text   = meal.name
        photoImageView.image = meal.photo
        ratingControl.rating = meal.rating
    }

    // Enable the Save button only if the text field has a valid Meal name.
    checkValidMealName()
}
```

运行app


![](/images/9-4.png)

##### 更新unwindToMealList(\_:)方法实现增加和更换meals

打开MealTableViewController.swift.找到unwindToMealList(\_:)方法，修改为如下
```
@IBAction func unwindToMealList(sender: UIStoryboardSegue) {
    if let sourceViewController = sender.sourceViewController as? MealViewController, meal = sourceViewController.meal {
        if let selectedIndexPath = tableView.indexPathForSelectedRow {
            // Update an existing meal.
            meals[selectedIndexPath.row] = meal
            tableView.reloadRowsAtIndexPaths([selectedIndexPath], withRowAnimation: .None)
        }
        else {
            // Add a new meal.
            let newIndexPath = NSIndexPath(forRow: meals.count, inSection: 0)
            meals.append(meal)
            tableView.insertRowsAtIndexPaths([newIndexPath], withRowAnimation: .Bottom)
        }
    }
}
```

运行app

![](/images/9-5.png)

### 取消已存在的meal的编辑

##### 改变cancel动作的实现

打开MealViewController.swift，找到cancel(\_:)方法，修改为如下
```
@IBAction func cancel(sender: UIBarButtonItem) {
    // Depending on style of presentation (modal or push presentation), this view controller needs to be dismissed in two different ways.
    let isPresentingInAddMealMode = presentingViewController is UINavigationController

    if isPresentingInAddMealMode {
        dismissViewControllerAnimated(true, completion: nil)
    }
    else {
        navigationController!.popViewControllerAnimated(true)
    }
}
```

### 支持meals 删除

##### 在table view中增加编辑按钮

打开MealTableViewController.swift，找到viewDidLoad() 方法，修改为如下
```
override func viewDidLoad() {
    super.viewDidLoad()

    // Use the edit button item provided by the table view controller.
    navigationItem.leftBarButtonItem = editButtonItem()

    // Load the sample data.
    loadSampleMeals()
}
```
运行app

![](/images/9-6.png)

##### 删除一个meal

打开MealTableViewController.swift，找到tableView(\_:commitEditingStyle:forRowAtIndexPath:)方法，修改为
```
// Override to support editing the table view.
override func tableView(tableView: UITableView, commitEditingStyle editingStyle: UITableViewCellEditingStyle, forRowAtIndexPath indexPath: NSIndexPath) {
    if editingStyle == .Delete {
        // Delete the row from the data source
        meals.removeAtIndex(indexPath.row)
        tableView.deleteRowsAtIndexPaths([indexPath], withRowAnimation: .Fade)
    } else if editingStyle == .Insert {
        // Create a new instance of the appropriate class, insert it into the array, and add a new row to the table view
    }
}
```
运行app

![](/images/9-7.png)
