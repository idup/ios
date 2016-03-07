title: Location
date: 2015-12-16 11:41:42
category: 应用示例
tags:
---

本教程主要介绍如何在应用中使用定位和地图技术。 相应代码位于 [https://github.com/idup/Location](https://github.com/idup/Location)

#### 1.新建项目

![](/picture/6-1.png)

新建项目，只需选择普通的SingleViewApplication即可

#### 2.编辑Storyboard

![](/picture/6-2.png)

在Storyboard中拖好页面及其对应控件，具体可参考Demo的storyboard，在本demo中主要由三个页面

1.一个页面用于显示CoreLocation获得的经纬度信息

2.一个页面用于显示MapView

3.还有一个页面用于显示地图的搜索结果

#### 3.创建ViewController

![](/picture/6-3.png)

创建不同的ViewController用以操纵页面控件，并且将代码与相应页面绑定


1.CoreLocationViewController与显示经纬度信息的页面绑定

2.MapViewControllerMapView与显示MapView的页面绑定

3.MapSearchResultTableViewController与显示地图的搜索结果的页面绑定

#### 4.修改info.plist文件

![](/picture/6-4.png)


在info.plist中添加两个字段，分别为NSLocationWhenInUseUsageDescription和 NSLocationAlwaysUsageDescription，并为其填入value，value的信息将会在申请定位权限时显示给用户

#### 5.ViewController代码编写

1.CoreLocationViewController中利用CoreLocation获得定位，并将获得的定位信息显示在页面上

2.MapViewController将用户的当前位置和用户的查找结果大头针显示在MapView
