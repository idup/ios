title: iOS应用基础
date: 2016-02-09 17:28:32
tags:
---

## iOS应用架构
一个iOS应用（App）是你所开发的代码和系统框架间交互过程的实现。系统框架提供应用运行所需的所有基础设施，你所写的代码提供了对基础设施个性化定制，实现了你所需要的用户交互界面和业务功能。

>本质上说，每个iOS应用都是一样的，你只是定义了一点特殊性。“我们不生产水，我们只是大自然的搬运工。”


iOS应用总体架构遵循MVC架构模式。
{% image /images/model_view_controller.png 500 "MVC" %}


具体而言，大部分iOS应用的结构如下图所示。

{% image /images/core_objects.png 500 "iOS应用结构" %}
