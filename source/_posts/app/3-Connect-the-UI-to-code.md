title: 三. 连接界面与代码
date: 2015-12-07 11:18:57
category:  iOS应用示例
tags:
---

### 为UI元素创建Outlets

点击toolbar中的Assistant按钮，将assistant editor从Preview状态转换为Automatic状态。

![](/images/3-1.png)

在代码区找到

```
class ViewController: UIViewController
```
在这行下添加标记,这个标记并没有什么用处，主要用来提供一些有用的文本信息

```
// MARK: Properties
```

在storyboard中选择text field,按住control键将它拖拽到代码区刚才添加的标记下面一行

![](/images/3-2.png)

在出现的对话框中输入nameTextField

![](/images/3-3.png)

点击链接，在代码区出现如下代码

```
@IBOutlet weak var nameTextField: UITextField!
```
以相同方式将label拖拽到代码区

![](/images/3-4.png)

### 定义执行操作

在 ViewController.swift代码区域中，在最后一个 } 前添加

```
// MARK: Actions
```
将Set Default Label Text按钮拖拽至标记下面

![](/images/3-5.png)

在方法中添加代码

```
@IBAction func setDefaultLabelText(sender:
   UIButton) {
    mealNameLabel.text = "Default Text"
}
```
标签值被修改

![](/images/3-6.png)

### 获取用户输入

采用UITextFieldDelegate协议，在UIViewController后添加UITextFieldDelegate

```
class ViewController: UIViewController,
UITextFieldDelegate {
```

设置ViewController作为nameTextField的委托, 对viewDidLoad()修改

```
override func viewDidLoad() {
    super.viewDidLoad()
    // Handle the text field’s user input through delegate callbacks.
    nameTextField.delegate = self
}
```

实现UITextFieldDelegate协议方法textFieldShouldReturn(\_:) 和 textFieldDidEndEditing(\_:)

```
func textFieldShouldReturn(textField: UITextField) -> Bool {
    // Hide the keyboard.
    textField.resignFirstResponder()
    return true
}
```

```
func textFieldDidEndEditing(textField: UITextField) {
    mealNameLabel.text = textField.text
}
```
运行模拟器查看结果
