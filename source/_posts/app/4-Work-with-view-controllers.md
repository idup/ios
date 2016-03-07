title: 四. 编写视图控制器
date: 2015-12-06 11:58:26
category:  IOS应用开发
tags:
---

### 增加一张Meal图片

从Object library中拖拽一个 image view放入stack view中的button下面。

![](/images/4-1.png)

在工具栏中选择 Size inspector菜单，将Intrinsic Size标签设置为Placeholder，并将宽度和高度设置为320

![](/images/4-2.png)

给图片增加约束条件，Pin菜单中勾选 Aspect Ratio.

![](/images/4-3.png)

 在工具栏的Attributes inspector菜单下找到Interaction标签，勾选User Interaction Enabled。

### 展示默认图片

在project navigator中选择Assets.xcassets。在左底角点击+符号，把图片拖入image set中的2*槽中，Attributes inspector中选择image，在列表中选择刚才添加的图片defaultPhoto。运行模拟器。

![](/images/4-4.png)

### 连接代码与图片

拖拽image view到ViewController.swift代码区，name为photoImageView

![](/images/4-5.png)

### 创建手势识别

从Object Library中拖拽一个Object Library，将其放在image view上添加一个点击手势识别。

![](/images/4-6.png)

![](/images/4-7.png)

### 将手势识别连接到代码区

拖拽 gesture recognizer到ViewController.swift代码区，name设置为selectImageFromPhotoLibrary，type设置为UITapGestureRecognizer

![](/images/4-8.png)

![](/images/4-9.png)

### 创建图像选择器来响应用户点击

在ViewController.swift代码区中修改相应代码
```
class ViewController: UIViewController, UITextFieldDelegate, UIImagePickerControllerDelegate, UINavigationControllerDelegate {
```
修改 selectImageFromPhotoLibrary(\_:)方法

```
@IBAction func selectImageFromPhotoLibrary(sender: UITapGestureRecognizer) {
    // Hide the keyboard.
    nameTextField.resignFirstResponder()

    // UIImagePickerController is a view controller that lets a user pick media from their photo library.
    let imagePickerController = UIImagePickerController()

    // Only allow photos to be picked, not taken.
    imagePickerController.sourceType = .PhotoLibrary

    // Make sure ViewController is notified when the user picks an image.
    imagePickerController.delegate = self

    presentViewController(imagePickerController, animated: true, completion: nil)
}
```
实现两个委托方法

```
func imagePickerControllerDidCancel(picker: UIImagePickerController)
func imagePickerController(picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [String : AnyObject])
```

imagePickerControllerDidCancel(\_:) 方法内容
```
func imagePickerControllerDidCancel(picker: UIImagePickerController) {
    // Dismiss the picker if the user canceled.
    dismissViewControllerAnimated(true, completion: nil)
}
```

imagePickerController(\_:didFinishPickingMediaWithInfo) 方法内容

```
func imagePickerController(picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [String : AnyObject]) {
    // The info dictionary contains multiple representations of the image, and this uses the original.
    let selectedImage = info[UIImagePickerControllerOriginalImage] as! UIImage

    // Set photoImageView to display the selected image.
    photoImageView.image = selectedImage

    // Dismiss the picker.
    dismissViewControllerAnimated(true, completion: nil)
}
```

运行模拟器

![](/images/4-10.png)

从电脑中向模拟器中拖拽图片，图片就会被添加进模拟器中

![](/images/4-11.png)

![](/images/4-12.png)

点击image view,选择向模拟器中添加的图片

![](/images/4-13.png)
