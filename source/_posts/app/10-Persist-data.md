title: 十. 持久化数据
date: 2015-12-00 12:00:00
category:  iOS应用示例
tags:
---

### 保存并加载Meal

##### 实现代码键结构
打开 Meal.swift，在// MARK: Properties下面增加如下结构
```
// MARK: Types

struct PropertyKey {
  static let nameKey = "name"
   static let photoKey = "photo"
   static let ratingKey = "rating"

}

```
在 Meal.swift中找到Meal class行,修改为
```
class Meal: NSObject, NSCoding {
```

##### 实现encodeWithCoder方法

打开Meal.swift，在代码最后一个 { 前面增加如下代码
```
func encodeWithCoder(aCoder: NSCoder) {
    aCoder.encodeObject(name, forKey: PropertyKey.nameKey)
    aCoder.encodeObject(photo, forKey: PropertyKey.photoKey)
    aCoder.encodeInteger(rating, forKey: PropertyKey.ratingKey)
}
```
##### 初始化加载meal

在encodeWithCoder(\_:)方法前，增加代码
```
required convenience init?(coder aDecoder: NSCoder) {
    let name = aDecoder.decodeObjectForKey(PropertyKey.nameKey) as! String

    // Because photo is an optional property of Meal, use conditional cast.
    let photo = aDecoder.decodeObjectForKey(PropertyKey.photoKey) as? UIImage

    let rating = aDecoder.decodeIntegerForKey(PropertyKey.ratingKey)

    // Must call designated initializer.
    self.init(name: name, photo: photo, rating: rating)
}
```
##### 更新初始化实现来调用父类的初始化

找到initializer并修改为如下
```
init?(name: String, photo: UIImage?, rating: Int) {
    // Initialize stored properties.
    self.name = name
    self.photo = photo
    self.rating = rating

    super.init()

    // Initialization should fail if there is no name or if the rating is negative.
    if name.isEmpty || rating < 0 {
        return nil
    }
}

```
##### 创建数据的文件路径

在 Meal.swift中，在 // MARK: Properties部分下面，增加如下代码

```
// MARK: Archiving Paths

static let DocumentsDirectory = NSFileManager().URLsForDirectory(.DocumentDirectory, inDomains: .UserDomainMask).first!
static let ArchiveURL = DocumentsDirectory.URLByAppendingPathComponent("meals")
```

### 保存并加载meal列表

##### 实现保存meal list的方法
打开MealTableViewController.swift，在最后一个 } 前增加如下代码
```
func saveMeals() {
    let isSuccessfulSave = NSKeyedArchiver.archiveRootObject(meals, toFile: Meal.ArchiveURL.path!)
    if !isSuccessfulSave {
        print("Failed to save meals...")
    }
}
```
##### 实现加载meal list的方法
打开MealTableViewController.swift，在最后一个 } 前增加如下代码

```
func loadMeals() -> [Meal]? {
    return NSKeyedUnarchiver.unarchiveObjectWithFile(Meal.ArchiveURL.path!) as? [Meal]
}
```

##### 保存列表当用户增加。移除或者编辑meal时

在MealTableViewController.swift中，找打unwindToMealList(\_:)方法， 修改为
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
        // Save the meals.
        saveMeals()
    }
```
找到tableView(\_:commitEditingStyle:forRowAtIndexPath:) 方法，修改为
```
// Override to support editing the table view.
override func tableView(tableView: UITableView, commitEditingStyle editingStyle: UITableViewCellEditingStyle, forRowAtIndexPath indexPath: NSIndexPath) {
    if editingStyle == .Delete {
        // Delete the row from the data source
        meals.removeAtIndex(indexPath.row)
        saveMeals()
        tableView.deleteRowsAtIndexPaths([indexPath], withRowAnimation: .Fade)
    } else if editingStyle == .Insert {
        // Create a new instance of the appropriate class, insert it into the array, and add a new row to the table view
    }
}
```
##### 在合适时间加载 meal list
在MealTableViewController.swift中，找到viewDidLoad() 方法，修改为如下
```
override func viewDidLoad() {
    super.viewDidLoad()

    // Use the edit button item provided by the table view controller.
    navigationItem.leftBarButtonItem = editButtonItem()

    // Load any saved meals, otherwise load sample data.
    if let savedMeals = loadMeals() {
        meals += savedMeals
    } else {
        // Load the sample data.
        loadSampleMeals()
    }
}
```
