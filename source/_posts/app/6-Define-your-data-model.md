title: 六. 定义数据模型
date: 2015-12-04 11:58:51
category:  IOS应用开发
tags:
---

### 创建数据模型

现在需要创建一个数据模型去存储 meal scene呈现的信息

##### 创建一个简单的数据模型类

依次点击File > New > File，选择ios下的source选项，选择Swift File,点击next，相关配置如下，点击完成，就创建了一个名为Meal.swift的文件

![](/images/6-1.png)

##### 为meal定义一个数据模型

打开Meal.swift.将import Foundation改为import UIKit

在import声明下，添加如下代码
```
class Meal {
    // MARK: Properties

    var name: String
    var photo: UIImage?
    var rating: Int
}
// MARK: Initialization

init?(name: String, photo: UIImage?, rating: Int) {
    // Initialize stored properties.
    self.name = name
    self.photo = photo
    self.rating = rating

    // Initialization should fail if there is no name or if the rating is negative.
    if name.isEmpty || rating < 0 {
        return nil
    }
}
```

### 测试数据

定义了数据模型，还没有完全并入你的app,你也不能保证所有的实现都是正确的，这时就可以通过单元测试来检验代码的正确性。

##### 查看单元测试文件

![](/images/6-2.png)

##### 编写单元测试

打开FoodTrackerTests.swift文件，删除模板测试代码，修改为如下测试代码

```
// Tests to confirm that the Meal initializer returns when no name or a negative rating is provided.
func testMealInitialization() {
    // Success case.
    let potentialItem = Meal(name: "Newest meal", photo: nil, rating: 5)
    XCTAssertNotNil(potentialItem)

    // Failure cases.
    let noName = Meal(name: "", photo: nil, rating: 0)
    XCTAssertNil(noName, "Empty name is invalid")

    let badRating = Meal(name: "Really bad rating", photo: nil, rating: -1)
    XCTAssertNotNil(badRating)
}
```
##### 运行testMealInitialization() 单元测试

在FoodTrackerTests.swift文件中找到testMealInitialization()单元，在测试名字左边找到一个棱形形状的标签，点击标签运行单元测试。

![](/images/6-3.png)

##### 修改测试案例

找到testMealInitialization()的最后一行，修改为

```
XCTAssertNil(badRating, "Negative ratings are invalid, be positive")
```
重新运行，所有样例都能测试通过

![](/images/6-4.png)
