title: Xcode概览
date: 2015-10-01 18:26:47
tags:
---
Xcode 概述 
<!--more-->

## 工作区窗口[The Workspace Window](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/TheWorkspaceWindow.html#//apple_ref/doc/uid/TP40010215-CH25-SW1)

***
### [Workspace Window Overview](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/TheWorkspaceWindow.html#//apple_ref/doc/uid/TP40010215-CH25-SW1)
***
Xcode工作区可用来执行核心开发任务，它是创建和管理工程的主界面。工程是Xcode开发中的主要单元，包含了构建应用程序所需的所有元素、框架、插件以及其他软件产品，并维系这着这些元素之间的关系。关于工程的更多详细信息，请参看： A Project Is a Repository of Files and Resources for Building Apps.

Xcode的工作区可以自动适应其手头上的任务，您可以更进一步配置窗口使之适合自己的工作风格。您可以根据需要打开多个工作区。

工作区窗口组件如下图所示：

![xcode1_1](/images/xcode1_1.png)

工作区窗口包含编辑区。当您选中工程中的一个文件时，其内容会出现在编辑区，Xcode会在适当的编辑器中打开文件。比如上图中，在工作区窗口左侧的导航器中选中一个Swift代码文件，右侧的编辑区则会包含AdventureScene.swift。

工作区窗口最多可展示3个可选区域，用于在开发周期中执行不同的任务。隐藏不用的区域可帮您更好地专注于当前的任务。您可以通过工具栏最右端的工作区配置按钮隐藏或者展示可选区。

XC_O_area_button_navigator_2x.png展示和隐藏导航区域（navigator area）。您可以在导航区遍历整个工程，包括文件、符号、断点、编译问题、测试以及编译报告等，也可以搜索工程中的任何字符串。

XC_O_area_button_debug_2x.png展示和隐藏调试区（debug area）。您可以在调试区查看变量，与调试终端进行交互，以及控制应用程序的执行。

XC_O_area_button_utilities_2x.png展示和隐藏实用工具区（utilities area）。您可以在该区域检查或更改文件的属性、图形UI元素、sprites以及项目中的其他元素，也可以用来访问现成的资源库，请参看： Access Resources and Inspect Elements in the Utilities Area.

### 在工作区导航[Navigating Your Workspace](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/NavigatingYourWorkspace.html#//apple_ref/doc/uid/TP40010215-CH26-SW1)

您可以在导航面板中访问工程中的文件、符号、单元测试、诊断以及其他方面。在导航栏中，您可以选择适合自身任务的导航器，并在每个导航器的内容区（content area）访问工程相关的部分，而且每个导航器的filter bar则可以让您限制内容的展示。

![xcode1_2](/images/xcode1_2.png)

Navigator bar中包含以下选项：

* XC_O_navigator_project_button_2x.png工程导航器（Project navigator）：在工程中添加、删除、分组以及管理文件，或者查看文件，或者在编辑区编辑其内容。

* XC_O_navigator_symbol_button_2x.png符号导航器（Symbol navigator）：以列表或者层级形式浏览工程中的符号。可通过Filter bar左侧的按钮将符号限制在任意类或者协议的组合，或者仅展示工程中的符号，或者仅展示容器（containers）。

* XC_O_navigator_find_button_2x.png搜索导航器（Find navigator）：使用搜索或者过滤功能快速查找工程中的任何字符串。

* XC_O_navigator_issue_button_2x.png问题导航器（Issue navigator）：可查看在打开、分析以及构建项目过程中发现的诊断、警告以及错误问题。

* XC_O_navigator_test_button_2x.png测试导航器（Test navigator）：创建、管理、运行以及检查单元测试。

* XC_O_navigator_debug_button_2x.png调试导航器（Debug navigator）：检查项目执行过程中某个指定点或指定时间的运行线程和相关的堆栈信息。

* XC_O_navigator_breakpoint_button_2x.png断点导航器（Breakpoint navigator）：通过指定特征（比如触发条件）来微调断点。

* XC_O_navigator_report_button_2x.png报告导航器（Report navigator）：查看构建、运行、调试、持续集成以及源码控制相关历史信息。

在Filter bar文本输入区键入文本，则会在内容区（Content area）展示包含该检索词的项目。大部分导航器在filter bar左侧展示按钮，用以进一步限制所展示的内容。部分filter bar左侧有一个“+”的按钮，可用来在content area中添加元素。报告导航器中filter bar左侧的按钮（XC_O_filter_bot_button_2x.png）用来与bots进行交互。关于报告导航器中Bots的用法详情请参看Xcode Continuous Integration Guide中Manage and Monitor Bots from the Report Navigator一节。

在Content area选中文件并查看或者编辑文件。

### 编辑工程文件[Editing Your Files](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/EditingYourFiles.html#//apple_ref/doc/uid/TP40010215-CH27-SW1)

Xcode中大部分编辑工作发生在编辑区，该区域是工作区窗口中主要的可视化区域。最常使用的编辑器有：

* 源码编辑器（Source editor）：用以编写源代码。

* Interface Builder：用以图形化地创建和编辑用户界面文件。

* 工程编辑器（Project editor）：用以查看和编辑应用程序的构建方式，比如制定构建选项、目标架构以及app entitlements。

在导航器的内容区选中文件，Xcode会在相应的编辑器中打开文件。在截图中，我们在project navigator中选择文件iPhoneStoryboard.storyboard，那么会在Interface Builder中打开该文件。Interface Builder在左侧展示大纲视图，并在右侧展示画布（canvas）。更多信息请参看Build a User Interface。（可选的实用工具区和调试区被隐藏，以便最大化导航器和编辑器的空间）

![xcode1_3](/images/xcode1_3.png)
以下截图展示了若干出现在搜索导航器内容区的搜索结果。选中其中一项结果，其文本字符串就出现在源码编辑器中。
![xcode1_4](/images/xcode1_4.png)

#### 配置编辑区域
使用工具栏右侧的编辑器配置按钮，并根据既定的任务来配置编辑区域。

* XC_O_editor_buttons_standard_2x.png标准编辑器（Standard editor）：使用选中文件的内容填充编辑区。

* XC_O_editor_buttons_assistant_2x.png辅助编辑器（Assistant editor）：在标准编辑器面板中展示一个逻辑上与内容相关的单独的编辑器面板。您可以更改其内容。

* XC_O_editor_buttons_version_2x.png版本编辑器（Version editor）：在一个面板中展示当前选文件，在第二个面板中展示该文件的另一个版本，以便比较两者之间的差异。只有当您的工程支持源码控制的时候，该编辑器才起作用。

下图是一个在标准编辑器面板中打开的执行文件APAAdventureScene.m。隐藏了导航区、调试区以及工具区3个可选的工作区，最大化了编辑区的内容展示。在源码编辑器中，辅助面板展示了执行文件相关的头文件APAAdventureScene.h.

![xcode1_5](/images/xcode1_5.png)

#### 使用跳转栏

每个编辑器或者辅助编辑器面板都包括一个跳转栏--一个交互式的分层机制，用以直接跳转至工程中任意层次结构中的某个项目。跳转栏的配置和行为可根据上下文环境

定制。一个基本的跳转栏配置由3部分组成：

1. 相关项目菜单（XC_O_jumpbar_related_button_2x.png）提供了与当前上下文环境相关的附加选项，比如最近打开的文件或者您正在编辑的执行（.m）文件的接口（.h）文件。

2. XC_O_jumpbar_next_prev_buttons_2x.png用来在导航历史中查看上一个或者下一个文件。

3. 分层路径菜单允许您通过跳转至一个新项目来更改编辑器或者辅助编辑器面板中展示的内容。根据您点击的路径，它可以由一个或者多个分段组成。


点击分层路径菜单中的某个分段（segment）可看到相关项目的弹出菜单。比如，如果分段可识别工程的名称，那您可以在工程中使用跳转栏导航至某个文件或者打开任何一个文件。如果分段可识别文件夹的名称，那您可以使用跳转栏打开文件夹内的文件。如果分段可识别源码文件的名称，那您可以在当前打开的文件中使用跳转栏来展示并选中符号。

![xcode1_6](/images/xcode1_6.png)

### 在实用工具区访问资源和检查元素

实用工具区位于工作区窗口的最右边，您可以通过它快速访问以下资源：

* Inspectors,用以查看和更改编辑器中打开的文件的属性（特性）。

* 现成的库-可用在工程中的现成库。

下图中，实用工具区面板的顶端是Inspectors，底部面板中放置的是可访问使用的库。
![xcode1_7](/images/xcode1_7.png)

使用inspector栏选择最适用于您当前任务的检查器。通常情况下，您通常会在检查器栏中看见两个检查器，其余检查器在其他编辑器中可见。

* XC_O_inspector_file_button_2x.png文件检查器（File inspector）：用以查看和管理选中文件的元数据。尤其是要本地化storyboards和其他媒体文件，并更改用户界面文件设置时。

* XC_O_inspector_quick_help_button_2x.png快速帮助（Quick Help）：查看符号的细节信息、界面元素，或者在文件中构建设置。比如Quick Help展示对方法的简明描述，该方法何时在何处被声明，该方法的范围，它所需的参数，以及适用平台和可用的架构。

使用library bar 访问现有的资源库：

* XC_O_inspector_file_button_2x.png文件模板（File templates）：普通类型文件和代码结构的模板。

* XC_O_library_code_templates_button_2x.png代码片段（Code snippets）：用以储存您软件中用到的源代码片段，比如类声明、control flows、block声明以及苹果公司常用的模板。

* XC_O_library_objects_button_2x.png（对象）Objects：应用程序用户界面的项目。

* XC_O_library_media_button_2x.png（媒体）Media：包含图形、图标、声音文件以及诸如此类的文件。

想要在您的项目中使用现成的库，可将其直接拖拽至适当的区域。比如，您要使用代码片段，可将其从库中直接拖放到源码编辑器中；想要使用文件模板创建一个源码文件，可将其模板拖放至工程导航器中。

想要限制某个被选中库的项目展示数，可在 filter bar的文本域输入相关的文本进行限制。比如，输入“button”来展示对象库中的所有按钮。

### 使用工作区工具栏管理常见任务
工作区窗口顶部的工具栏可让您快速访问频繁使用的命令。“Run”按钮可构建和运行您的产品。“Stop”按钮可终止代码的运行。“Scheme menu”可让您配置您想要创建和运行的产品。“Activity viewer”通过展示状态信息来展示当前任务执行的进程、构建进程以及您项目的其他信息。

到此，您已经清楚了编辑器配置按钮如何配置编辑器区域，已经了解了工作区配置按钮如何隐藏或者展示可选的导航器区、调试区以及实用工具区。

![xcode1_8](/images/xcode1_8.png)

View菜单包括隐藏或者展示工具栏的命令。

![xcode1_9](/images/xcode1_9.png)

### 使用多个Tab或者多个窗口

使用Safari风格的tab来实现工作区窗口多重的工作流指定的布局。比如，在下方的截图中，活跃标签展示了资源编辑器中执行文件(APAViewController.m) 的内容，右端的是头文件(APAViewController.h)，左边是app storyboard(iPhoneStoryboard.storyboard)。点击某个tab，其对应的编辑器则会成为当前的活跃编辑器。

![xcode1_10](/images/xcode1_10.png)

View菜单包含了展示和隐藏tab的命令。创建一个tab，可选择File > New > Tab。想要移除tab，请将指针放在tab上并点击关闭按钮即可。

想要创建多个工作区窗口，可选择 File > New Window。可定义每个tab或窗口，比如使用工具栏中的Hide/Show实用工具按钮(XC_O_utilities_button_2x.png )展示或隐藏实用工具区。

![xcode1_11](/images/xcode1_11.png)

![xcode1_12](/images/xcode1_12.png)


## 创建应用Creating Apps
***

### 管理工程 [Working with Projects](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CreatingProjects.html#//apple_ref/doc/uid/TP40010215-CH31-SW1)
***
在Xcode中创建的应用程序需要一个“project（项目）”来组织必需的文件和资源。您可以通过选择 File > New > New Project 来创建一个新的项目。Xcode将会打开一个新的工作区窗口并显示一个对话框，来让您选择一个合适的项目模板。Xcode为iOS和Mac应用程序开发提供了许多常见样式的内置模板。这些模板包含了必要的项目配置和文件，以帮助您快速启动开发工作。

![xcode2_1](/images/xcode2_1.png)

您可以在项目导航栏查看项目文件的名称。当您在项目导航栏选中了一个文件，该文件的内容将会显示在合适的编辑器或查看器中。下方的屏幕截图展示了Adventure项目。在项目导航栏中选中一个实现文件（APAViewController.m），该文件内容则显示在源码编辑器中。

![xcode2_2](/images/xcode2_2.png)


#### 项目中存放着搭建应用程序所需的文件和资源([A Project Is a Repository of Files and Resources for Building Apps](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CreatingProjects.html#//apple_ref/doc/uid/TP40010215-CH31-SW1))
***
项目包含了搭建一个或多个应用（或者其他软件产品，例如命令行工具以及插件）所需的元素。项目同样还维护着这些元素之间的关系。这些元素包括了：

* 源代码文件（包括相应的实现文件和头文件）、库和框架、图片文件和用户界面文件。
* 在项目导航器中负责组织文件架构的组文件夹（Groups）。
* 项目级别的应用编译配置。
* 产生单个应用的对象（Targets）。

选中项目导航器中的项目名称，则打开项目编辑器。您可以使用编辑器来确定如何编译应用程序，从SDK版本到指定编译器选项。在这张截图中，我们选中了项目导航器中的Adventure项目并打开了项目编辑器，项目编辑器展示了Adventure项目的信息面板。

![xcode2_3](/images/xcode2_3.png)

创建项目后，Xcode会提供两个标准项目级的编译配置：调试和发布。这些配置的不同之处主要在于它们是否包含调试信息，以及版本优化程度。这两项编译默认配置应该足以满足您的产品开发需求。一般情况下，开发者不必更改编译设置。

要添加更多的编译配置项，可打开项目编辑器，复制项目现有配置中的某项配置，然后修改它的设置。例如，您可以配置一个包含调试信息的全面优化编译设置，以便于调试优化代码。

![xcode2_4](/images/xcode2_4.png)

#### 打开关闭工程或者工作区([Closing and Opening a Project or a Workspace](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CreatingProjects.html#//apple_ref/doc/uid/TP40010215-CH31-SW1))

要关闭一个项目或工作区，选择 File > Close Project or File > Close Workspace 。Xcode将会记住您曾经打开过的窗口以及它们的配置情况，当你重新打开项目或工作区后则恢复这些配置。

### 管理对象 [Working with Targets](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/WorkingwithTargets.html#//apple_ref/doc/uid/TP40010215-CH32-SW1)

每个项目都至少包含一个对象（target）。一个target可指定构建的产品，比如是一个iOS或Mac应用。在项目编辑器中选中一个target来查看和修改其设置。在下面的截图中，Adventure项目的Adventure iOS target在项目编辑器中被选中。该项目编辑器显示了该对象的General面板。

![xcode2_5](/images/xcode2_5.png)

对象的General面板显示了一些您偶尔会检查并可能修改的基本设置。在应用开发过程中，您通常在其他地方修改这些值，比如说，在创建一个新项目时出现的对话框中设置。

对于iOS应用来说，General面板中包含的对象设置有：

* bundle Identifier：包标识符，这是一个让操作系统和App Store识别应用的字符串。
* Version : 发布应用程序的版本号。
* Build：内部版本号，它标识了应用程序的某个特定版本。
* Team：加入了苹果开发者计划的开发团队的名称。
* Deployment Target：即应用最低能够运行的iOS版本。
* Devices：能够运行应用的设备
* Main Interface：应用启动时预加载的主用户界面。
* Devices Orientation：应用程序支持的用户界面方向（纵向，上下颠倒，横向左置，横向右置）

对于watchOs应用，General面板中包含的对象设置有：

* 应用名称
* 包标识符
* 版本号
* 内部版本号
* app图标


对于Mac应用来说，General面板中包含的对象设置有：

* 应用类别，用来在Mac App Store中应用分类
* 包标识符
* 版本号
* 内部版本号
* 可选值，内容要么是Mac App Store中的签名代码，或者是在Mac App Store外分发的某个开发者ID的签名代码，或者是未签名符号。
* 部署对象，即应用最低能够运行的OS X版本
* OS X中用来让用户识别应用程序的icon

有关调试或发布应用的具体信息，请参阅Run Your App.

#### 向对象中加入苹果提供的技术 *Adding Technology Features to a Target*
***
要向应用中添加各种各样的苹果技术，比如说iCloud、游戏中心、应用内购买以及地图等等，那需要在项目编辑器中选中对象，然后单击Capabilities选项。通过打开功能的开关来向应用中添加功能。Xcode将会向您的项目中添加必要的权益（entitlements）文件，并将必要的框架链接到target上。在某些情况下，Xcode中可能会碰到激活功能失败方面的问题。如果碰到此类问题的话，出错信息将被显示在该功能中的信息区域中。

您可以通过单击功能名称左边的三角形按钮来显示或隐藏功能细节。当功能未激活时，该区域大致描述了该功能和激活该功能时的操作。当功能激活时，可使用该区域查看或更新相关的配置，并鉴定需要修复的
问题。

![xcode2_6](/images/xcode2_6.png)

有关添加功能的更多信息，请参见App Distribution Guide中Adding Capabilities一节。

#### 向对象中添加文件类型和服务信息  (*Adding File Type and Service Information to a Target*)
***
对象的Info面板显示了和应用程序相关的属性，以及应用程序能够创建或打开的文件类型，并且对于OS X来说，还显示了应用程序所能提供的服务。绝大多数的自定义对象属性可在Xcode界面的其他部分进行修改（比如说在General面板中设置的包标识符、版本号以及内部版本号）。下面的截图显示了Adventure应用iOS对象的Info面板。

![xcode2_7](/images/xcode2_7.png)

文档类型设置指定了能够在应用中创建和编辑的文档类型，并且提供了可在iOS或Mac OS中展示的代表该文档类型的自定义图标。

您可以为应用程序添加输出和导入UTI（统一类型标识符）来让其能够导入或者输出任何文件类型。和专用于应用程序的文档类型不同，UTI指定了某些通用的格式，比如说纯文本或者.png。举个例子，UTI支持在应用间使用剪贴板复制和粘贴。想获得关于支持类型列表的相关信息，请参见Uniform Type Identifiers Reference.

URL类型设置允许您通过使用自定义协议为应用间交换的数据指定自定义schemas。例如一些现有的schemas，比如HTTP、mailto以及SMS。欲了解更多信息，请参阅App Programming Guide for iOS (iOS)中的Using URL Schemes to Communicate with App一节，或者参阅Launch Services Programming Guide(Mac OS)。

Mac OS应用使用出现在Services菜单上的Services项目来添加新的项目。欲了解更多信息，请参阅“Services Implementation Guide”。

#### 给对象重写编译设置 (*Overriding Build Settings for a Target*)
***
对象中包含了编译应用的指令——以编译设置和编译阶段的形式。target继承了项目的编译设置。虽然绝大多数开发者很少需要更改这些设置，但是您仍然可以通过在对象层面确定不同的设置项来重写项目的所有编译设置。在项目编辑器中选中一个对象，然后在Info、Build Settings或者Build Phases面板中修改项目设置。



### 使用工作区来处理关联项目 [Working on Realated Projects](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/WorkingonRelatedProjects.html#//apple_ref/doc/uid/TP40010215-CH33-SW1)
***
工作区是项目的集合，它可以降低大型应用程序的复杂性。工作区具有以下几个优点：

工作区的所有项目都可以访问同一工作区的其他项目，包括编译信息。
您可以设置项目之间的依赖关系，这样一个简单的编译命令就可以编译所有选中对象所需的片段。
您可以将静态库或模块包含进工作区，无论是您自己的还是第三方的。
您可以将大项目分解成更小的项目，使功能维护和共享更加方便。
通过选择 File > New > Workspace 来创建一个工作区。当创建一个工作区后，您可以在其中创建新项目，并且可以向其中添加现有项目。在创建工作区后，请打开工作区文件，而不是打开项目文件。

现有的项目转换成工作区请选择 File > Save As Workspace 。该项目的当前窗口将被转换到工作区窗口。

以下屏幕截图显示了包含两个Xcode项目文件的工作区示例。导航区最上方的那个项目是一个名为MySharedFramework的框架。另外一个项目文件是一个应用程序，名为UsesSharedFramework，其中包含了共享的框架。使用工作区可以让应用项目能够访问共享的框架中的所有文件，同时也让诸如调试之类的任务更加轻松。添加该框架到应用程序为应用程序和框架之间创建了一种依赖关系。Xcode在应用编译之前检查框架是否需要编译。

![xcode2_8](/images/xcode2_8.png)


## 在源码编辑器中编写代码 [Writing Code](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingandOpeningFiles.html#//apple_ref/doc/uid/TP40010215-CH35-SW1)

***
### 打开和添加文件 [Opening and Adding Files](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingandOpeningFiles.html#//apple_ref/doc/uid/TP40010215-CH35-SW1)
***

要查看和编辑源码文件，请在工程导航器中选中文件，文件的内容则会展示在工作区窗口的编辑区域。

![xcode3_1](/images/xcode3_1.png)

#### 通过模板来创建源文件 *Creating Source Files from Templates*
***
使用文件模板来添加文件到您的项目中是最省心的办法。要访问文件模板库，请单击工作区窗口的实用工具区的文件模板按钮![xcode3_2](/images/xcode3_2.png)，并将这些模板拖曳到项目导航器中来创建源文件。

![xcode3_3](/images/xcode3_3.png)

可以选择 File > New File 或者使用 Command + N 的快捷键来创建源文件。Xcode 将打开一个 New File 对话框，您可以从中选择合适的模板来创建文件。选择完模板后单击 Next 按钮，给文件命名后就可以将其添加到项目中了。

![xcode3_4](/images/xcode3_4.png)

![xcode3_5](/images/xcode3_5.png)

#### 快速打开文件 *Opening a File Quicking*
***
选择 File > Open Quickly 来查找一个定义特殊符号的文件，也可以选择一个名称含有特定字符的文件。Open Quickly 搜索栏不区分大小写，并且搜索范围仅限于当前项目和已激活的软件开发包（SDK）。您可以在搜索结果列表中双击文件来打开它们。
![xcode3_6](/images/xcode3_6.png)

要打开辅助编辑器窗格中的文件，请在双击时按住 Option 键。要在一个单独的窗口中打开文件，请按下Option + shift 键。要查看能让您指定应在何处打开文件的对话框，请按住 Option + shift 键并单击。

#### 拆分编辑器窗口来显示相关内容 *Splitting the Editor to Display Related Content*

***
拆分编辑器窗口以便能够查看一个文件的多个视图，亦或者是能一次查看多个相关文件。例如，您可以同时查看某个实现文件以及其对应的头文件。要拆分代码编辑器，可点击工作区工具栏上的辅助编辑器按钮（![xcode3_7](/images/xcode3_7.png)）来打开辅助编辑器窗口。您可以选择垂直拆分还是水平拆分。

![xcode3_8](/images/xcode3_8.png)
![xcode3_9](/images/xcode3_9.png)

如果要改变拆分的方向的话，选择 View > Assistant Editor，然后选择其中一项菜单设置。在上面两个截图中，我们关闭了导航栏和工具栏以最大程度地显示代码编辑器区域。

#### 设置辅助编辑窗口 *Setting the Assistant Editor Mode*
***

当打开辅助编辑器窗口时，您可以将其设置为两种模式：手动或跟踪。在手动模式下，您通过跳转栏选择要显示的文件。即使您改变了主编辑器的内容，辅助编辑器中的内容也不会改变。

在跟踪模式下，您可以从弹出菜单中选择一种标准。这个标准含有一些内含组，比如说副本、父类、子类以及同级类。一旦您选中了一个标准，那么 Xcode 将会在子菜单中列出相应的文件。当您改变了主编辑器中的文件时，Xcode就会基于选中的标准来更新辅助编辑器。

要更改模式，请选择辅助弹出菜单中的某一项。（辅助弹出菜单是辅助编辑器跳转栏中前进和后退按钮右边的第一个项目）

![xcode3_10](/images/xcode3_10.png)

您可以通过点击辅助编辑器窗格右上方的添加按钮![xcode3_12](/images/xcode3_12.png)来进一步分割辅助编辑器窗格。一旁的关闭按钮![xcode3_12](/images/xcode3_12.png)则将其关闭。

![xcode3_11](/images/xcode3_11.png)

### 编辑源代码 [Editing Source Code](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/EditingSourceCode.html#//apple_ref/doc/uid/TP40010215-CH34-SW1)
***

#### 键入时修正错误 *Fix Errors as You Type*
***
当你在源码编辑器中进行输入时，Xcode会对文本进行扫描。当你出现语法错误时，Xcode会以红色下划线或者插入符号标记。点击错误之处，Xcode则会展示对问题的描述信息。

![xcode3_13](/images/xcode3_13.png)

通常，Fix-it可自动修复错误。选中推荐的修复方案，按下Return键接受修复。在上方的屏幕截图中，Fix-it建议在文本字符串之前插入“@”字符。更多信息，请查看 Catching Mistakes with Fix-it.

#### 使用代码补全功能加快输入 *Speed Up Typing with Code Completion*
***
当您开始键入某个符号名符号时，Xcode 会提供内联建议以补全其名称。单击建议栏中的某项来选中它，或者使用向上或向下键来更改选中的建议。按下 Return 键接受该建议。

![xcode3_14](/images/xcode3_14.png)

当一个方法或者函数含有参数或者引用时，代码完成功能将用占位符来替代每个参数。要在这些占位符中跳转，请选择 Navigate > Jump to Next Placeholder（或者 Navigate > Jump to Previous Placeholder）。另外，使用 Tab 键可以跳转到下一个占位符，Shift + Tab 键跳转到上一个占位符。

#### 自动配对花括号、圆括号以及方括号 *Match Pairs of Braces, Parenthese, and Brackets Automatically*
***
Xcode 帮助您自动配对分隔符，比如：

* 将鼠标指针放在源代码编辑器左边缘的焦点范围带上。Xcode 高亮显示该位置的括号范围，如前面的屏幕截图所示。
* 键入一个左括号，Xcode 将会在键入换行符之后插入右括号。
* 键入一个右括号或者其他分隔符，Xcode 将简要强调其对应的分隔符。
* 使用向右箭头键将插入点移动到结束分隔符后面，Xcode会暂时高量强调其对应的分隔符。
* 选择 Editor > Structure > Balance Delimiter。Xcode 将选择插入点附近的文本，其中包括最近的一组封闭分隔符。
* 双击任意一个分隔符。Xcode 将选中由分隔符以及其对应分隔符所封闭的全部文本。


#### 在您的文件中插入代码片段 *Drop Code Snippets into Your Files*
***
您可以使用代码片段快速键入源码文本。您可以从Code Snippet Library中直接将代码片段拖放至源码文件中。想要访问Code Snippet Library，请在工作区窗口的实用工具区点击Code Snippet标识按钮（04.png）。Code Snippet Library提供了有用的标准的代码片段，比如屏幕上展示的switch语句代码片段。想要将自己的代码片段添加至代码片段库中，并添加快捷键，请查看Source Editor Help.

![xcode3_15](/images/xcode3_15.png)

#### 使用手势和快捷键 *Use Gestures and Keyboard Shortcuts*
***

使用手势和快捷键可以简化并增强您对源代码编辑器的使用。除了在 OS X 系统上常见的 Multi-Touch 手势，下列这些手势在源代码编辑器中尤为适用：

* 两指轻按可以打开编辑器的上下文菜单（还可以通过Control-click或使用鼠标左键单击显示）
* 两指向上或向下轻扫垂直滚动，以及左右水平滚动。
* 三指轻扫导航栏可以在编辑器中打开任何文件。向左轻扫显示前一个文件，向右轻扫显示后一个文件。

键盘序列提供了很多在 Xcode 中常见的菜单命令快捷键。例如，按住 Shift + Command + O 键可以从 File 菜单中调用 Open Quickly 命令，按住 Shift + Command + D 键可以从 Navigate 菜单中调用 Jump 命令。还有一些在编辑操作中的快捷键。例如，Control + K 可以删除从插入点到行尾的所有字符。

快捷键通过键值绑定来建立，您可以选择 Xcode > Preferences 然后选择 Key Bindings 来查看和修改快捷键。

### 搜索和替代 [Search and Replace](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/SearchandReplace.html#//apple_ref/doc/uid/TP40010215-CH36-SW1)
***

Xcode 提供了几种方法来适用于多行文本修改。

#### 文件中替代 *Searching in a File*
***
通过选择 Find > Find and Replace 来更改一个文件中的文本字符串实例。

![xcode3_16](/images/xcode3_16.png)

#### 编辑所有的符号 *Editing All Symbols*
***
您可以同时修改某一范围内出现的所有相同的符号名称，比如说局部变量或者参数名。将插入符放在您想要编辑的符号上，当三角形符号出现时，单击它来显示出菜单，然后选择 Edit All in Scope。接下来编辑该符号。当您输入新的内容后，该符号的所有实例都将同时改变。

![xcode3_17](/images/xcode3_17.png)


#### 项目中替代 *Searching the Project*
***
您可以通过选择项目中的 Find > Find and Replace 项来改变项目或者工作区中的文本字符串实例。这个命令将显示查找导航器。您可以自定义其操作--例如限制搜索范围，或者按大小写来匹配字符串。查找导航器提供了一个预览，允许您替换字符串的所有实例或者接受还是拒绝某一单独替换。

![xcode3_18](/images/xcode3_18.png)

#### 使用字符串模式 *Using Wildcards*
***

您可以在搜索区使用通配符字符串模式。要进入该模式的某个部分，单击查找检索区左侧的小三角形，然后选择 Insert Pattern 。从模式弹出菜单中选择一项。Xcode 将在查找到的字符串中的当前光标位置插入该通配符。

![xcode3_19](/images/xcode3_19.png)

#### 重构代码 *Refactoring Code*
***

您可以重构您的代码以改善其结构、增强易读性和可维护性而不改变其行为。重构操作（也称为变换）被应用到您在代码编辑器中选择的某个代码片段或符号上。您可以重命名符号、提取代码并放到方法中、创建父类、移动项目到父类或子类，以及在整个项目文件范围内封装变量。

在选择完需要重构的代码片段或符号后，选择 Edit > Refactor，然后选择合适的重构命令。预览面板将显示应用重构时代码会出现的变化。在预览对话框的左窗格中取消某个文件可以将其从重构操作中移除。您可以在预览中直接编辑您的源代码。所有的修改操作将在预览中显示，并且其会包含在重构操作中。

![xcode3_20](/images/xcode3_20.png)

### 管理符号 [Working with Symbols](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/WorkingwithSymbols.html#//apple_ref/doc/uid/TP40010215-CH37-SW1)
***

#### 显示符号的定义 *Display the Definition of a Symbol*
***

将鼠标指针放到一个符号上，然后按住 Command 键并单击来显示这个符号的定义。源代码编辑器将导航到该符号的定义中，并将其高亮显示。如果该定义位于单独的文件中，那么代码编辑器将会显示这个文件（亦或者将鼠标指针放到符号上，然后选择 Navigate > Jump to Definition）。

将鼠标指针放到一个符号上，然后按住 Command + Option 键并单击，就可以在辅助编辑器窗格中显示其定义，如截图中所示的APALoadFramesFromAtlas函数。这个方法可以让您在查看符号定义时保持该符号一直在视图中。

![xcode3_21](/images/xcode3_21.png)

#### 查看某个符号的相关文档 *Look Up Documentation for a Symbol*
***

您可以通过将插入点放到符号上来查看其参考文档，比如说方法或属性。在检查器窗格工具栏中选择 Quick Help 按钮（）。如果检查器窗格没有打开，那么可在主工具栏中单击该按钮来以在工作区配置按钮集中显示该导航。符号的 Quick Help 项出现在工具区。

文档信息包括针对该符号的完整参考文档链接、声明该符号的头文件、相关的编程指南、以及相关的示例代码。（按住 Option 单击该符号，以查看弹出窗口中的信息概要，即声明、符号的描述信息、其所有返回值、其可用的 SDK版本、头文件以及相关参考文档的链接）。

![xcode3_22](/images/xcode3_22.png)

单击 Quick Help 中的链接，Xcode 将会打开一个单独的 Xcode 文档查看器窗口。Xcode 的文档查看起提供了访问信息的快捷步骤，而无需将您的注意力从正在编辑的文件中离开。

![xcode3_23](/images/xcode3_23.png)

除了详细的框架API参考外，文档查看器还包括苹果工程师提供的完整编程指南、教程、示例代码以及视频演示。在类引用中单击靠近查看器顶部的“More related items（更多相关项）”来跳转到与您的任务相关的另一个文件中。

![xcode3_25](/images/xcode3_25.png)

使用工具栏上的搜索栏来查找关于 API 或者编程概念的额外信息。

要在一个消息中内含一个指向该文档的链接，单击分享按钮![xcode3_24](/images/xcode3_24.png)，然后选择电子邮件链接或信息。您可以在 Safari 中以 HTML 或 PDF 格式打开。对于示例代码项目来说，单击窗口顶部的 Open Project 来下载该项目然后在 Xcode 中打开.

![xcode3_26](/images/xcode3_26.png)

### 分析您的代码 [Analyzing Your Code](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AnalyzingYourCode.html#//apple_ref/doc/uid/TP40010215-CH38-SW1)
***

#### 使用代码折叠来检查代码 *Examining the Structure of Your Code with Code Folding*
***

您可以通过隐藏源代码的其他部分，来让自己更容易将注意力集中在源代码的特定函数或方法上。选择 Editor > Code Folding > Fold Methods & Functions。定位到您想要折叠的方法上，然后双击它的省略按钮来折叠该方法。下面的截图显示了configureConnectedGameControllers方法的折叠。

![xcode3_27](/images/xcode3_27.png)

将鼠标指针移动到编辑器左边缘上，它将会在焦点框中显示一个焦点范围带——比如说截图中的for声明。范围外的代码将会用阴影覆盖。

#### 进行静态代码分析 *Performing Static Code Analysis*
***

您可以在运行应用前使用静态分析器查找代码中的bug。静态分析器可在数秒内尝试上千种可能的代码路径，然后报告可能隐藏得很深的错误，或者是几乎不可能被复制的 bug。静态分析器同样还将确定出您代码中没有遵守 API 推荐使用方式的区域，比如Foundation、UIKit 以及AppKit 等API的语言风格。

要执行静态代码分析的话，请选择 Product > Analyze。Xcode 的静态分析器将解析程序的源代码，并确定这些问题类型：

* 逻辑错误，如访问未初始化的变量和取消对空指针引用。
* 内存管理错误，如分配内存泄露
* 死存储（未使用的变量）错误
* 由不遵循项目正在使用的框架和库所需的策略所引发的 API 用法错误。

静态分析器将在问题导航栏中报告错误，您可以在项目导航栏中单击问题导航栏按钮来激活这个视图。在问题导航栏中选择一个分析器消息，以在源码编辑器中显示相关的代码。在源码编辑器中点击相应的消息，然后使用源码编辑器上方的分析结果栏中的弹出菜单来研究错误路径和原因。接着编辑代码以修复错误。

### [Customizing the Editor](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CustomizingtheEditor.html#//apple_ref/doc/uid/TP40010215-CH39-SW1)
***

#### 选择字体和文本颜色 *Choosing Syntax-Aware Fonts and Text Colors*
***

Xcode 基于编程语言来分析代码，并为每个标记或字符串分配一个句法标签。例如，项目中的每一个注释、关键字以及类名都将被定义。Xcode 为每个句法标签类型分配一种颜色和字体以让代码易于阅读。您可以通过选择 Xcode > Preferences 然后选择 Fonts & Colors 项来选择多种字体和颜色。例如，Presentation 主题增加了字体大小以让屏幕上的项目文本更易阅读。您可以创建自定义的字体和颜色主题。

![xcode3_28](/images/xcode3_28.png)

#### 自定义编辑和缩进选项 *Customizing Editing and Indenting Options*
***
您可以更改源代码编辑和缩进设置，以适应您的喜好。选择 Xcode > Preferences，然后选择 Text Editing 来修改如下配置：

* 在源代码编辑器边列显示行数
* 在您输入后自动插入右括号
* 当您输入代码时显示代码补全建议
* 使用空格或制表符缩进
* 虚换行(soft-wrap)线
* 执行语法感知缩进

### 获取编辑器帮助 [Finding Editor Help](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/FindingEditorHelp.html#//apple_ref/doc/uid/TP40010215-CH40-SW1)

***
可以在 Xcode 中直接显示步进说明，以帮助执行常见的源码编辑器任务。在源码编辑器的任意位置按住Control单击，便可以在一个列表中查看一系列常用指令。选择 Show All Hlep Topics 以查看所有关于源代码编辑器的帮助文章。选择某一项任务，然后帮助文章将会出现在 Xcode 的文档查看器窗口中。

![xcode3_29](/images/xcode3_29.png)

您可以在Xcode中使用快捷菜单获得Xcode帮助文章。在主界面任何地方按下Control键并单击鼠标，则可以看到适用于该区域的帮助文章列表。

![xcode3_30](/images/xcode3_30.png)

## 构建用户界面 [Building a User Interface](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UsingInterfaceBuilder.html#//apple_ref/doc/uid/TP40010215-CH42-SW1)
***

### 使用Interface Builder [Using Interface Builder](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UsingInterfaceBuilder.html#//apple_ref/doc/uid/TP40010215-CH42-SW1)
***

开发者可使用Interface Builder创建应用程序的用户界面。在工程导航器中打开一个界面文件，文件内容会在工作区窗口的编辑区域的Interface Builder中打开。用户界面文件的扩展名为.storyboard或.xib，xib文件通常会指定一个视图控制器或菜单栏，storyboard文件则指定了一系列视图控制器及其跳转关系。与xib不同，storyboard可以包含用户界面所有的视觉元素。当你使用Xcode内建的模板创建新工程时，会提供一个默认的用户界面文件。

![xcode4_1](/images/xcode4_1.png)

code以 XML格式储存xib和storyboard文件内容。编译时，Xcode将xib和storyboard文件编译成二进制文件，即nib文件。运行时，nib文件会被载入并实例化来创建新的视图。

想要添加用户界面元素，可从实用工具区将元素拖放至Interface Builder画布上，你可以在此对齐元素，为其设置属性，以及为元素之间和源码文件中的代码建立联系。在Interface Builder中布局好界面所需元素后，你可以在辅助编辑器中编写代码实现其行为。

![xcode4_2](/images/xcode4_2.png)

#### IB的组成部分 *Parts of Interface Builder*
***

Interface Builder有两个主要区域，左边的dock栏和右边的canvas。dock栏列出了用户界面文件包含的对象，canvas用于对app用户界面中的对象进行布局。

![xcode4_3](/images/xcode4_3.png)

dock栏中的大纲视图展示了更高级别对象中嵌入的对象。

![xcode4_4](/images/xcode4_4.png)

对于xib文件，你可以点击Interface builder左下角的Show Document Outline按钮(DockViewControl)，从而以icon视图形式展示高级对象，而不是大纲视图。

![xcode4_5](/images/xcode4_5.png)

对于storyboard文件，大纲视图的顶级项目对应画布上的顶级视图控制器或场景。隐藏大纲视图后，Storyboard文件则不会展示icon视图。Storyboard上的每个场景在画布上都有一个对应的高级对象视图，如下图所示，icon视图中的项目从左到右依次对应场景、场景中的first responder以及该场景的退出segue。更多信息详见Design the User Interface of Your App with Storyboards.

![xcode4_6](/images/xcode4_6.png)



#### 添加界面对象 *Adding Interface Objects*
***

要往用户界面中添加内容，先点击工作区窗口中工具栏的按钮打开实用工具区，然后点击工具库栏中的按钮调出对象库，然后选择一个对象拖入到视图中，在下图中，我们从对象库中拖放一个视图控制器到画布上。

![xcode4_7](/images/xcode4_7.png)

添加对象后，你可以拖住其边角来改变其大小。移动对象时，会出现一些蓝色虚线来帮助你定位和布局对象。在对象库栏上方是Interface Builder检查器，你可以用它设置对象外观和行为，在下图中，我们用属性检查器（Attributes Inspector）按钮(AttributesInspectorSelected)指定按钮的自定义类型

![xcode4_8](/images/xcode4_8.png)

#### 查找和替代字符串*Finding and Replacing Strings*
***

### 使用storyboard来设计应用的界面 [Designing with Storyboards](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/DesigningwithStoryboards.html#//apple_ref/doc/uid/TP40010215-CH43-SW1)
***
您可以使用storyboard来可视化地布局用户在iOS或Mac 应用中的路径，使用Interface Builder按照下述内容指定用户界面：

* 场景
* 场景间切换
* 触发场景切换的控件

场景表示屏上内容区域。在iPhone或iPod touch上面，一个屏幕通常只包含一个场景。在iPad或Mac上面，一个屏幕可以由一个以上的场景组成。Segue表示一个场景到另一个场景的切换。

下图表示了使用Xcode 的Master-Detail应用模板创建iOS项目时所提供的默认storyboard，它包含三个场景和两个segue。最左边的场景是一个导航控制器，用于管理用户在主界面和详细页间的导航。使用这个模板时，你可以按需从对象库中添加额外的视图控制器，并使用Identity inspector配置拖放到画布中的视图控制器。

从对象库中拖放对象到每个场景中，并使用Attributes inspector配置对象和界面之间的切换。

![xcode4_9](/images/xcode4_9.png)

你的主视图可能包含一个表格，表格中有多个条目，每一个条都有一个对应的详情场景来提供条目的具体信息。导航控制器提供了返回到主视图的返回按钮.

![xcode4_10](/images/xcode4_10.png)

### 连接代码和界面对象 [Connecting Objects to Code](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/ConnectingObjectstoCode.html#//apple_ref/doc/uid/TP40010215-CH44-SW1)
***

通过编写代码来实现界面对象的行为。代码通过动作和outlet连接来与界面对象沟通。

创建一个动作连接，控件就可以给代码发送消息了。控件是一种用户操作时产生即时动作或视觉效果的界面元素。例如，当用户点击一个按钮时，按钮会给代码发送一个动作消息来执行相应的动作。文本框、滑动条和开关都是iOS中常用的控件；复选框、滚动条以及文本框是Mac OS中常用的控件。

当您需要从代码给界面对象发送消息时，可创建一个outlet连接。对象可以是控件，也可以是storyboard 或 xib文件中定义的其他对象，例如一个标签、进度指示器或是地图视图。如果代码决定一个按钮需要消失，那么代码可以通过outlet发送消息告知按钮应当隐藏。


#### 通过控制器给代码发送消息 *Sending Action Messages from a Control to Your Code*

当用户点击控件并与之进行交互时，控件就会给代码发送消息来执行特定的动作。配置控件给代码发送动作信息的最简单方式是按下Control键，并用鼠标从Interface Builder中将控件拖到工程的执行文件中。

当Interface Builder在标准编辑器面板中打开时，选中你想要配置的控件，并点击辅助编辑器按钮打开项目的实现文件。

按下Control键，并用鼠标从Interface Builder中将控件拖到工程的执行文件中（图中辅助编辑器展示了Warrior按钮的视图控制器的执行文件），Xcode会提示你在代码的哪个位置插入动作方法。

![xcode4_11](/images/xcode4_11.png)

松开鼠标后，辅助编辑器会弹出一个Connection菜单，你可以输入动作方法的名称（下图中方法名称为chooseWarrior），然后点击连接。

![xcode4_12](/images/xcode4_12.png)

在实现文件里，Xcode为新方法插入了一个骨骼动画定义，如下所示。IBAction返回类型是一个特殊的关键字，表示这个实例方法可以连接到storyboard或xib文件。Xcode同时会配置控件，从而在选中事件发生时调用该方法。因此，只要控件收到一个动作信息，这个方法就会被调用。

![xcode4_13](/images/xcode4_13.png)

在这个骨骼动画定义中，你可以添加动作方法的源码。控件由系统激活，不过由你实现其行为。你在下面的图片中，当用户点击Warrior按钮时，这个动作方法会启动一个新游戏。

![xcode4_14](/images/xcode4_14.png)

#### 通过Outlet给界面元素发送消息 *Sending Messages to a User Interface Object Through an Outlet*
***

要通过代码给用户界面元素发送消息（比如通知标签展示文本字符串，通知按钮展示或者隐藏），你需要将界面元素和代码中的Outlet连接起来。最简单的方法是Control-点击-拖动画布上的UI对象到实现文件或头文件中。例如，要在试图控制器中创建一个outlet，并将其和按钮连接，你需要按下Control键并拖动IB中的按钮，将其放到辅助编辑器中视图控制器的实现文件中。Xcode会提示你在哪里插入是合适。

![xcode4_15](/images/xcode4_15.png)

释放Control拖动后，辅助编辑器会显示一个Connection菜单，选择Outlet，然后输入Outlet的名字（下图中Outlet的名字是warriorButton），点击Connect即可。

![xcode4_16](/images/xcode4_16.png)

Interface Builder会将Outlet的声明添加到类中（Outlet被定义为IBOutlet属性，IBOutlet关键字会告知Xcode该属性可以被连接到storyboard或xib文件中）

![xcode4_17](/images/xcode4_17.png)

### 适应不同的屏幕大小 [Building for Multiple Screen Sizes](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/BuildingforMultipleScreenSizes.html#//apple_ref/doc/uid/TP40010215-CH45-SW1)

#### 使用Size Classes类来适应不同的屏幕尺寸和设备持有方向 *Using Size Classes*

Size Classes 可以让你用一个storyboard来应对不同尺寸的屏幕。你需要建立一个界面，使得它可以在多数设备上运行，当屏幕大小改变时，只需更改需要变化的对象即可。

Size Classes会规定高和宽的一个相对的显示空间大小，这个大小可以是compact（紧凑型）或regular（常规型）。一般来说，iPhone竖屏时宽度是compact，横屏时高度是compact。iPhone竖屏时高度是regular，对于iPad，宽和高都是regular。具体的点数并不重要，相对的空间是重要的。

因为多数界面的显示对compact或regular选择都是一样的，因此还有一个额外的size class --any。你可以把compact和regular下一样的界面设为any，对于那些需要改变的再另外指出。Size Classes已知属性包括：

* 约束的常量
* 表明视图层次是否包含约束的布尔值
* 文本标签、文本域、文本视图或者按钮上的字体。

改变这些属性会导致界面的变化：

* 改变视图的大小或位置
* 添加或删除视图
* 添加或删除约束
* 改变文本标签、文本域、文本视图或者按钮上的字体。

需要注意的是，如果一个视图或布局约束在当前的size class下是不可用状态，也就是没有被装载到当前的size class中，这并不意味着该视图和布局约束的实例不存在，而是在它们出现时就已经被实例化了。无论哪种size class引用该视图或布局约束都会得到一个有效的对象。Xcode中的视图对象（不论是按钮还是图片，它们都是视图对象）都不会在界面层面有父视图对象，所以如果你卸载了一个视图，那么Xcode会相应的卸载掉与该视图相关的所有布局约束。

要为你的storyboard启用size classes，需要先在项目导航器中选中storyboard文件，然后在canvas面板的文件查看器那一栏的Use Size Classes复选框上打对勾。Xcode会询问你是否转换文件。打开size classes的同时会开启Auto Layout。

![xcode4_18](/images/xcode4_18.png)

启用size classes后，Xcode将以正方形在画布上展示所有顶层视图控制器。画布底部中心位置还有一个size classes的控件，该控件显示了当前size classes的宽高设置。在该示例中，它是any/any.

![xcode4_19](/images/xcode4_19.png)

如果要更改size classes，可点击下面的size classes控件，在弹出的菜单中移动鼠标，直到选中你想要的size classes为止。

![xcode4_20](/images/xcode4_20.png)

当你对size classes做出调整后，试图控制器的大小会相应改变，同时底栏也会变成蓝色，以提示你不在any/any的模式。

![xcode4_21](/images/xcode4_21.png)

你在一个特定size class中对约束、视图和字体做出的更改都仅限于该s类。要删除一个约束或视图，请选中它然后按下Command+Delete组合键。关闭一个视图后，你往往希望关闭与它相关的所有约束。

#### 界面元素布局的自动调整和定位 *Using Auto Layout for Automatic Resizing and Positioning*

自动布局可以帮你适应不同的窗口尺寸、屏幕尺寸以及设备持有方向。您可以通过给视图对象添加关系约束来实现。例如，你可以将一个图像在 storyboard场景中水平居中，当用户旋转设备时，图像会自动在新的布局中保持水平居中。

通过Auto Layout 约束来管理布局，界面中的元素会在以下情形中自动改变大小和位置：

* 用户改变了设备朝向
* 用户在Mac应用中改变了窗口大小
* 内容尺寸改变（例如字符串长度改变）

按下Control键并在两个界面对象间进行拖动，Interface Builder会弹出一个适当的约束列表，从列表中选择其中一项即可为项目添加约束。下图展示了从主logo视图拖放对象至控制器主视图的结果。弹出菜单显示了image view与容器间的两种约束选项。"Top Space to Container"是指图像视图与容器顶部之间的高度约束，另外一个约束定义了容器中图像水平居中。

![xcode4_22](/images/xcode4_22.png)

要查看一个对象的限制，可从大纲视图中选中该对象，或者在画布上选中该对象，出现的绿色实线则代表对象的约束，你可以点击尺寸查看器来查看约束列表。
![xcode4_23](/images/xcode4_23.png)

约束部分顶部形象化地展示了选中对象的约束类型，每条水平或者竖直的绿色实线表示一条或多条该类型约束。选择一条或多条实线可以筛选出符合该类型的约束列表。

![xcode4_24](/images/xcode4_24.png)

你可以在画布上选中约束，或者在Size inspector中双击约束来查看和编辑约束，再或者可以双击约束调出弹出编辑器来更改最常用的约束属性。

![xcode4_25](/images/xcode4_25.png)

还有更多的方法可以添加和编辑约束，包括使用底栏的按钮
![xcode4_26](/images/xcode4_26.png)

### 查看对象的文档 [Viewing Object Documentation](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/LookingupObjectDocumentation.html#//apple_ref/doc/uid/TP40010215-CH46-SW1)
***

您可以在Interface Builder中查看界面对象简略的类参考文档，而无需离开Interface Builder。

在文件打开的状态，点击按钮打开实用工具区，然后在检查器一栏选中Quick Help按钮。然后在Interface Builder点击你想要的对象的信息，文档会出现在工具区的检查器窗口中。

![xcode4_27](/images/xcode4_27.png)

如果要查看完整的详细文档，你需要点击 Quick Help中参考文档的标题，详细的参考文档会在新的文档查看窗口中打开。你还可以查看相应的编程指南、示例代码和其他相关文档。

如果要查看设置选项的更多信息，你需要将鼠标移动到该选项的上面，然后就会弹出一个帮助标签。

![xcode4_28](/images/xcode4_28.png)

## 预览您的用户界面 [Previewing Your User Interface](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/PreviewingYourUserInterface.html#//apple_ref/doc/uid/TP40010215-CH47-SW1)
***

使用内置的预览辅助编辑器可以预览您的用户界面在不同设备和使用不同语言，而不用编译您的应用程序。

![xcode4_29](/images/xcode4_29.png)

## 创建和绘制自定义的视图类 [Creating and Rendering Custom View Classes](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CreatingandRenderingCustomViewClasses.html#//apple_ref/doc/uid/TP40010215-CH48-SW1)
***

你可以把自定义的视图类在设计时使用在界面生成器。您还可以添加属性的自定义视图类属性检查器。

![xcode4_30](/images/xcode4_30.png)

## 使用Interface Builder获得帮助 [Finding Help for Interface Builder](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/FindingHelpforInterfaceBuilder.html#//apple_ref/doc/uid/TP40010215-CH49-SW1)
***

Xcode中提供了Interface Builder常见操作的详细步骤帮助。在Interface Builder画布中任意位置按住Control然后点击鼠标，就会出现一个菜单，里面列出了常用操作，选择 Show All Help Topics 就可以显示源码编辑器的所有帮助文章。

![xcode4_31](/images/xcode4_31.png)

因为Control-click这个操作在Interface Builder中用来创建连接，因此你必须在画布上执行Control点击来调出包含帮助文章列表的快捷菜单，而不是点击用户界面中的任意对象。

选中一个主题，帮助文章就会显示在Xcode文档查看器中。

![xcode4_32](/images/xcode4_32.png)


## 添加资源 [Adding Assets](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingImages.html#//apple_ref/doc/uid/TP40010215-CH50-SW1)
***

### 添加图像 [Adding Images](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingImages.html#//apple_ref/doc/uid/TP40010215-CH50-SW1)
***

为了更好地帮助您创建应用以及管理用户界面元素，除了Interface Builder之外，XCode 还提供了其他的工具来达成这个目的。

您可能会为应用添加许多图像，包括为不同的iOS设备准备的图标、自定义图片以及启动界面。其中一些图片向 App Store 提交时需要的。Asset catalog（资源目录）可以帮你很好地管理这些内容。

![xcode5_1](/images/xcode5_1.png)

借助粒子发射编辑器，您可以通过添加诸如雪花、火花和烟雾等可移动粒子在内的动画效果来增强您的应用程序。这些特效对于 iOS 和 Mac 上的游戏来说特别有用。

![xcode5_2](/images/xcode5_2.png)

#### 添加应用图标和启动界面 *Adding App Icons and Launch Image*
***

您需要为您应用所支持的所有操作系统版本和设备添加相应的应用图标。iOS 应用和 Mac 应用所需的图标种类不同。对于这两个平台来说，请在 Xcode 中的 asset catalog 中添加应用图标所需的版本。

对于 iOS 应用程序来说，所添加的应用图标将显示在设备的主屏幕和 App Store 上。Xcode 没有提供能创建图标的图形制作工具，请使用专门的设计软件来进行制作。请创建出一些在不同场景下使用的图标。您的 iOS 应用包含一个小图标（当显示搜索结果时使用）和一个高分辨率图标（用在有 Retina 显示屏的设备上）。如果您的 iOS 应用部署目标是通用的话，您还可以创建适用于 iPad 和 iPhone 设备上的图标版本。

对于 Mac 应用程序来说，创建一组图标集，包括为每个图标大小创建的图标对（标准和高分辨率）。以像素为单位就是：16 x 16, 32 x 32, 128 x 128, 256 x 256, 以及512 x 512。Finder 将使用这些图标来向用户显示您的应用

#### 使用Asset Catalog 中的图片资产 *Work with Image Assets in the Asset Catalog*
***

当您创建完新的项目之后，Xcode 将会创建一个名为`Images.xcassets`的资产目录。在项目导航栏中选中asset Catalog，然后 Xcode 就会在编辑区打开它。

Asset catalog 包含了一个图片集列表。每一个图片集（比如说截图中的 AppIcon）都包含了所有的图片版本，以支持不同的设备和分辨率。您可以通过将图标拖曳进合适的图标格子中，来向您的应用中添加图标。

![xcode5_3](/images/xcode5_3.png)

您可以在应用中为诸如按钮或者其他控件创建额外的图片集。要创建一个空图片集或者要向新图片集中导入图片，请单击位于图片集列表底部的 Add 按钮（+）。

#### 创建并设置 iOS 启动界面（或者启动界面文件） *Create and Set the iOS Launch Screen File*

***

当您在 iOS 上启动您的应用时，启动界面会首先显示出来。启动界面会在用户单击应用图标之后即刻显现，然后它会一直停留，直到您的主界面显示出来。如果您的应用在 iOS 8 或者更高版本运行，系统将采用一个 xib文件作为启动界面，并且根据屏幕大小来显示合适的尺寸。如果是要在 iOS 8 之前的版本进行开发，那么您就必须要向 asset catalog 中添加一系列的启动图片，以适应所有可能的屏幕尺寸。

新项目创建的时候会同时创建一个启动界面文件，名为`LaunchScreen.xib`。您也可以自行创建启动界面文件，选择 File > New，然后选中 User Interface category，接下来选择 Launch Screen 这个文件类型。启动界面文件使用 size classes 来适应不同屏幕尺寸和方向。

由于启动界面是在您应用运行前显示的，因此您只能使用 UIView 或 UIViewController 类型的唯一根视图。您同样也只能使用不需要更新的 UIKit 类。

要设置启动界面，请打开编译对象的 General 信息栏，然后从弹出菜单中选择启动界面文件。


#### 为 iOS 7 以及更早版本创建并设置iOS启动图片 *Create and Set iOS Launch Images for iOS 7 and Earlier*
***

您可以在一个设备上轻易地捕捉到启动图片的截图。您可以在设备上配置好您想要屏幕显示的方式，然后同时按下设备的锁定键以及 Home 键。然后您的截图就被保存在照片应用中的相机胶卷中。将这个截图从您的设备中拷贝到 Mac 上。比如说您可以使用 iPhoto 应用来完成这个操作，将屏幕截图从设备中导入，然后在以 PNG 格式导出到 Mac 上。

要将该截图设置为启动图片，选择项目导航栏中的 asset catalog 文件，然后选择 LaunchImage 图片集。将您的截图拖曳到合适的单元格中。

### 添加例子发射特效 [Adding Particle Emitter Effects](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingParticleEmitterEffects.html#//apple_ref/doc/uid/TP40010215-CH51-SW1)

***

Sprite Kit 提供了渲染图形和动画的基础设备，这个功能对 iOS 和 Mac 的游戏开发者来说特别有用。这种基础设置包括了粒子发射器。粒子发射器可以轻松制作小到一个几乎不动的粒子，大到成千上万个在屏幕上飞舞的小颗粒。您可以使用它来模拟火、雨、烟雾、雪花、火焰等动画效果。

XCode 提供了8个粒子发射器模板和一个用来操纵粒子外观和行为的编辑器。

在 Xcode 中使用 New Project 模板来创建一个 基于 Sprite Kit 的游戏，或者使用在项目编辑器中的General 窗格来向一个已存在的编译对象中添加 Sprite Kit 框架。要向您的项目中添加一个粒子发射器，请选择 File > New > File，然后选择 Resource > SpriteKit Particle File。

![xcode5_4](/images/xcode5_4.png)

然后从下拉菜单中选择例子发射器模板，单击下一步，在 Save As 区域中输入发射器的名称。接着选择在编译对象去中的和您项目相关的复选框。Xcode 将会创建一个带有.sks后缀的文件。

在项目导航器中选中您的粒子发射器文件，然后 Xcode 将会在粒子发射编辑器中打开这个文件。

![xcode5_5](/images/xcode5_5.png)

使用粒子发射检查器（ParticleEmitterInspector）来修改和检查粒子的效果。例如，您可以更改创建粒子的速度，粒子的样式，以及例子在创建后的行为。对检查器中所做的更改将立即生效，并可以在编辑器中查看。

### 向Mac应用中添加3D场景 [Adding 3D Scenes](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/Adding3DScenes.html#//apple_ref/doc/uid/TP40010215-CH52-SW1)

SceneKit 是为 Mac 应用准备的 3D 渲染框架。Sprite Kit 支持导入、处理和渲染 3D 项目，而不需要您拥有丰富的 3D 图形编程技能。借助 Scene Kit 编辑器，您可以预览 3D 场景，检查您源代码中需要的信息，以及调整场景对象的参数，以为您的应用加强和微调渲染效果。

要向项目中导入数字资源交换(digital asset exchange, DAE)文件，请使用项目导航栏。选择一个您想保存该文件的文件夹，然后选择 File > Add Files，然后选择该文件单击 Add。要在 Xcode 中浏览 3D 场景，在项目导航栏中选择这个 DAE 文件。Xcode 将在 Scene Kit 编辑器中打开这个文件。

要预览该场景并运行动画，使用 Scene Kit 编辑器主区中控制命令。按下 Play 按钮来播放动画，按下 Pause 按钮来暂停动画，然后滑动滑动条来滚动这个动画。使用触控板或者鼠标来操作这几点。

在工具区的检查器允许您查看并编辑位于场景图像列表或示例对象的节点信息。例如，借助与检查器相关的节点，您可以调整相机、光线或者集合属性，同样借助资源检查器，您可以调整资源上的许多设置和属性，比如说为其选择一个照明模型和一个内容文本。

![xcode5_6](/images/xcode5_6.png)

### 向Mac应用中添加数据文件 [Adding Data Sets](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingDataSets.html#//apple_ref/doc/uid/TP40010215-CH72-SW1)

***
![xcode5_7](/images/xcode5_7.png)

### 向Mac应用中添加[Watch Complications](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/AddingWatchComplications.html#//apple_ref/doc/uid/TP40010215-CH73-SW1)

![xcode5_8](/images/xcode5_8.png)

## 运行您的应用 [Running Your App](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/BuildingYourApp.html#//apple_ref/doc/uid/TP40010215-CH53-SW1)
***

### 生成您的应用 [Building Your App](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/BuildingYourApp.html#//apple_ref/doc/uid/TP40010215-CH53-SW1)
***
要编译并运行您的 iOS 或 Mac 应用，请在工作区的工具栏上选择一个编译方案，然后选择运行目标，接着单击 Run 按钮。单击 Stop 按钮即可使应用退出。

![xcode6_1](/images/xcode6_1.png)

如果您要运行 iOS 应用，Xcode 便会通过 iOS 模拟器或者是连接到 Mac 的 iOS 设备来启动它。而如果您要运行 Mac 应用的话，Xcode 会直接在 Mac 上运行它。

#### 选择一个Scheme来生成应用 *Choosing a Scheme to Build Your App*

编译方案(scheme)是一系列设置的集合，它指定构建项目的对象、所使用的编译配置，以及当应用启动时需要的运行环境。当您打开一个现有项目（或者创建一个新的项目）时，Xcode 将会自行为每个对象创建一个编译方案。默认的编译方案名称和您项目的名称相同，并且包含了五个运行操作的设置项：

* 运行应用
* 针对对象的运行单元测试
* 描述应用的性能特性的简介
* 为代码执行静态分析
* 归档应用应用为分发做准备，比如说分发给测试者或者上传到 App Store

每项操作都能生成应用，并将其作为可执行项目来运行。要选择编译方案，请使用在 Xcode 工作区工具栏上的Scheme menu。（您可以同样使用编译方案菜单来选择运行目标。）

#### 选择一个目标来运行应用 *Choosing a Destination to Run Your App*
****
当您生成应用的时候，运行目标（destination）将决定当应用生成完毕后其在何处运行。对于 Mac 应用来说，运行目标就是生成应用的这台 Mac 电脑。对于 iOS 应用来说，运行目标可以是连接至 Mac 的已配对 iOS 设备，也可以是 iOS 模拟器。iOS 模拟器和 iOS SDK 一起伴随着 Xcode 安装到您的 Mac 上，它可以在 Mac 上运行，并且可以模拟 iPhone 或者 iPad 的运行环境。

![xcode6_2](/images/xcode6_2.png)

Scheme菜单可以让您自由组合编译方案和运行目标，但是这两个设置是截然不同的。编译方案和运行目标并没有从属关系。在上述的截图当中，编译方案是 Adbenture iOS，运行目标是 iPhone Retina (4-inch) 模拟环境。其结果是 Adventure iOS 编译方案生成一个在模拟的 iOS 设备上运行的 iOS 程序。如下图所示，同一个编译方案可以在不同的运行目标上运行，比如说在模拟的 iPad 或在真机上运行。

![xcode6_3](/images/xcode6_3.png)

### 在模拟器中运行 [Running in the Simulator](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/RunningintheSimulator.html#//apple_ref/doc/uid/TP40010215-CH54-SW1)
***

iOS 模拟器允许您模拟一系列的 iPhone 和 iPad 设备，也可以模拟不同版本的 iOS 操作系统。您可以用键盘以及触控板来与 iOS 模拟器交互，来模拟单击、设备旋转，以及其他操作。例如，您可以使用 iOS 模拟器中的 Hardware 菜单来：

* 向左或向右旋转模拟器
* 模拟用户摇动设备
* 给前台应用发送一个模拟的内存不足警告

作为在真机测试前的初始工具，iOS 模拟器是您在整个开发流程中测试应用原型好工具之一。虽然您可以在 iOS 模拟器中测试您应用的基本操作，但是 iOS 模拟器作为一个测试平台仍然是有许多限制。在开发应用的过程中，真机测试是必不可少的。

![xcode6_4](/images/xcode6_4.png)

#### 创建自定义模拟器配置 *Create Custom Simulator Configurations*
***
选择 Window > Devices 来打开设备管理器。单击管理器窗口左下角的添加按钮（+）。在出现的对话框中，输入您自定义模拟器配置的名称，然后选择一个 iOS 版本。单击 Create ，这样您的自定义模拟器配置就被添加到模拟器列表中了。默认情况下，新的配置出现在运行目的目标菜单中。

![xcode6_5](/images/xcode6_5.png)

#### 在运行目标菜单中显示模拟器或真机 *Show Simulators or Devices in the Run Destinations Menu*
***
选择 Window > Devices。在设备管理器中，选择您想要在对象菜单中添加或者移除的设备。然后选择管理器窗口左下方的配置按钮选择 Show in Run Destinations Menu。旁边的复选标记将表明该设备或者模拟器是否会显示在运行目标菜单中。

![xcode6_6](/images/xcode6_6.png)

### [Running on a Device](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/RunningonaDevice.html#//apple_ref/doc/uid/TP40010215-CH55-SW1)
***
Xcode 在您的开发 Mac 环境上启动 Mac 应用。

![xcode6_7](/images/xcode6_7.png)


开发过程中，要在真机（iPad、iPhone或者 iPod touch）上运行 iOS 应用，需要如下四个条件：

设备需要连接至 Mac
您是苹果开发者项目的成员
您拥有一个开发者项目的有效签名证书
设备被开发者项目使用，且已被配置为可开发
如果您有条件没有满足，那么 Xcode 将会引领您进行修复，并且通常可以添加签名身份以及设备配置文件。

开发过程中，要在真机（iPad、iPhone或者 iPod touch）上运行 iOS 应用，设备必须连接到 Mac，并且该设备必须被苹果认证为可开发。如果您的 Mac 应用使用特定的 App 技术--如 iCloud，Game Center以及 In-App Purchase，那么您的 Mac 必须被认证。

苹果实现了一个基本的安全模型来保护用户数据，并且保护您的应用程序以防其在不知情的情况下被修改或被分发。在整个开发过程当中，您将创建资产（assets）并输入信息，让苹果用来验证识别您身份、您的设备以及您的应用。这些资产包括配置文件，用来确定您的开发设备。

要获得一个设备的配置文件，您需要成为苹果开发者计划的成员并且获得相应的签名身份。

#### 为运行目标选择设备 *Choosing Your Device for the Run Destination*
***


### 编辑、创建以及管理编译方案 [Managing Schemes](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/ManagingSchemes.html#//apple_ref/doc/uid/TP40010215-CH56-SW1)
***

要编辑编译方案，在编译方案菜单中选择 Edit Scheme。编译方案配置对话框的左边栏列出了编译方案能够执行的操作。您可以修改每个操作的设置。在截图中，Run 操作被修改为在 Xcode 运行应用时模拟 Mexico City 这个地点。

![xcode6_8](/images/xcode6_8.png)

您可以修改编译方案以让其执行下述操作：

* 生成多个目标
* 在某个操作执行前或执行后运行某个脚本
* 在某个操作执行前或执行后发送邮件
* 使用内存管理诊断来运行应用
* 为某个操作设置为调试(debug)或发布(release)，例如下面这个截图所示的 Run 操作。

创建新的编译方案的最便捷方式是单击编译方案复制按钮，这个按钮使用可用的编译方案作为模板来让您可以重命名、编辑以及保存一个新的编译方案。如果您创建了一个编译方案，就可以通过单击位于编译方案配置对话框中的管理方案按钮。或者如下面截图所示的通过选择编译方案菜单中的 Manage Schemes。您可以重命名编译方案，也可以重新组织其在编译方案菜单中显示的方式。您也同样可以指定该编译方案是否可以在菜单中显示，指定该编译方案应该被存储在项目或者是工作区的何种位置，以及指定该编译方案是否可以被共享，比如说团队成员从源代码库中访问项目。您可以单击 Autocreate Schemes Now 按钮来让 Xcode为没有编译方案的对象自行创建编译方案。


![xcode6_9](/images/xcode6_9.png)

## 调试 [Debugging](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UsingtheDebugger.html#//apple_ref/doc/uid/TP40010215-CH57-SW1)

***
### 使用 Debugger [Using the Debugger](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UsingtheDebugger.html#//apple_ref/doc/uid/TP40010215-CH57-SW1)
***
当您点击了工作区工具条中的运行按钮并且你的应用编译成功，那么Xcode运行您的应用程序并开启调试功能。您可以使用图形化的工具直接在源码编辑器中调试应用，比如使用Data tips、快速查看(Quick look)来查看变量值。

调试区域(Debug area)和调试导航器(Debug navigator)可以让您检查运行中的app的状态，并控制其执行。

![xcode7_1](/images/xcode7_1.png)

为了创建一个高质量的应用，要尽可能减少应用对用户系统的影响。使用调试导航器（Debug navigator）中的调试仪表（Debug gauges）深入了解你应用的资源消耗，当你发现问题时，请使用Instruments确认并分析应用的性能。

如果你正在开发一款iOS应用，在设计和早期测试阶段可以使用iOS模拟器找出存在的问题。

你可以配置Xcode来帮助你专注于调试任务。举例来说，当代码运行到一个断点时，你可以让Xcode自动播放一次警告声，并创建一个命名为的Debug标签的窗口，Xcode可在此展示调试区(Debug area)、调试导航器(Debug navigator)以及断点处的代码。


#### 控制执行 *Controlling Execution*
***

code允许您一行一行单步调试你的代码来查看特定执行阶段中应用的状态。使用调试区域(Debug area)来控制代码的执行，观察程序的变量和寄存器，观察控制台的输出并且与调试器交互。 你也可以使用调试区导航渲染帧的OpenGL调用，并查看特定调用的渲染状态信息。

通过点击工作区窗口工具条上视图选择器的中间按钮来展示调试区域(Debug area)。

![xcode7_2](/images/xcode7_2.png)

#### 查看状态信息 *Viewing State Information*
***

点击调试区工具栏中的暂停按钮（在暂停和继续之间切换）来暂停app的执行。想要设置断点，只需要打开源代码文件，并且点击你想暂停执行代码所在行的边列（Gutter）。边列中一个蓝色箭头会标识断点。如果想了解更多关于断点的信息，包括如何设置断点行为和不同类型的断点，请查看Breakpoint Navigator Help.

暂停应用后，当前正在执行的代码行会用绿色高亮。你可以使用调试区顶部条上的Step Over、Step Into、Step Out三个按钮来单步调试代码的执行。Step Over会执行当前行的代码行，包括任何的方法。如果当前的代码行调用了一个方法，step into会开始执行当前代码行，然后在到达被调用方法的第一行时停止。Step Out则执行当前方法或函数的剩余部分。

当暂停执行时，调试导航器会打开并展示一个堆栈追踪。选中其中一项，在编辑区和调试区中查看该项目的信息。当你调试时，可展开或收起线程来显示或隐藏堆栈框架。

![xcode7_3](/images/xcode7_3.png)

将指针悬停在源代码编辑器中的任何变量上，可查看一个显示着变量值的数据提示。点击变量旁边的Inspector图标(QuickLookInspectorIcon)，将对象的Objective-C描述打印至调试区控制台，并在一个额外弹出视图中展示。

![xcode7_4](/images/xcode7_4.png)

点击Quick Look图标(QuickLookVarIcon)观察变量内容的图形化展示。你可以针对自己的对象实现自定义的快Quick Look。

![xcode7_5](/images/xcode7_5.png)

####  查看内存越界 *Finding Memory Corruption*
***

![xcode7_6](/images/xcode7_6.png)

![xcode7_7](/images/xcode7_7.png)

#### *Debugging Metal*

#### *Debugging OpenGL*

当你在设备上构建并运行一个OpenGl ES应用时，调试区工具栏会包含一个Frame Capture 按钮（ ）。点击该按钮来捕捉一个frame。你可以使用OpenGL ES帧捕获做以下事情：

* 检查OpenGL ES 状态信息

* 内省OpenGL ES 对象，比如视图纹理和着色器。

* 在每次绘制调用之前单步调试状态调用，然后观察每个调用的变化。

* 单步调试绘制调用以准确查看如何构建图像。

* 在辅助编辑器中查看每个绘制调用使用哪些对象。

* 编辑着色器以查看应用程序上的效果。

以下截图展示已渲染帧的组件。左侧调试导航器显示部分渲染树，主调试器显示已渲染帧的颜色和深度资源，并展示其他一些图片资源。

![xcode7_8](/images/xcode7_8.png)


### 在运行时检查你应用的视图层次 [Examining the View Hierarchy](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/ExaminingtheViewHierarchy.html#//apple_ref/doc/uid/TP40010215-CH58-SW1)
***

点击在调试区顶栏的Debug View Hierarchy按钮来检查当前暂停应用的3D渲染视图分层。你可以：

* 通过在画布中点击并拖动来旋转该透视图。

* 使用左下方的滑动条增大或减小各视图层之间的间距。

* 使用右下方双滑块的滑动条改变可见视图的范围。滑动左滑块来改变最底层可见的视图，滑动右滑块来改变最上层可见的视图

* 按下展示剪切内容按钮来显示选中视图中被裁减的内容。

* 按下展示约束按钮来显示选中视图的任何Auto Layout约束。

* 使用放大（+）按钮和缩小（—）按钮来增加或减少透视图的放大倍数。

![xcode7_9](/images/xcode7_9.png)

### 检查应用对系统资源的影响 [Examining System Impact](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/ExaminingSystemImpact.html#//apple_ref/doc/uid/TP40010215-CH59-SW1)
***
调试导航器（Debug navigator）提供了能对应用程序性能进行深度分析的仪表。比如CPU仪表计量器展现了app的CPU的使用率，方便你侦测异常情况。根据应用的目的和功能，仪表计量器可以告诉你应用对内存、iCloud、OpenGL ES、电量以及CPU的影响。

![xcode7_10](/images/xcode7_10.png)

如果想要看详细的报告，可单击调试区的某个仪表计量器。如果你想要对你应用做更深层次的分析，请点击Profile In Instruments按钮。

![xcode7_11](/images/xcode7_11.png)

在问题区，电量报告会提供一个初步的诊断来告知你什么可能在严重损耗你的用电量。

![xcode7_12](/images/xcode7_12.png)

### 测量应用程序的性能 [Measuring Performance](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/MeasuringPerformance.html#//apple_ref/doc/uid/TP40010215-CH60-SW1)
***

Xcode中的Instruments程序会从在运行的应用中收集数据，并且展现在一个图形化的时间线上。使用Instruments，你可以收集性能方面的数据，比如你应用的内存使用，磁盘活动情况，网络活动情况和图形操作。通过把数据放在一起查看，你可以分析你应用表现的各个方面来找出潜在提升性能的可能。你也可以自动化测试iOS应用的界面元素。

![xcode7_13](/images/xcode7_13.png)

在Xcode几种方法来打开Instruments，比如：

* 从仪表计量器详细报告界面点击Profile in Instruments 按钮

* 选择Product>Profile

* 在一个scheme中的Profile项中指定一个Instrument

Instruments程序使用名为instruments的单独的数据采集模块，来随时收集某个进程的数据。Instruments程序有一个模板库，每个模板包括了为获取相关信息的一系列instruments。

![xcode7_14](/images/xcode7_14.png)

### 模拟问题 [mulating Problems](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/SimulatingProblems.html#//apple_ref/doc/uid/TP40010215-CH61-SW1)

***

iOS模拟器可帮你在设计和早期测试阶段找到主要的问题。举例来说，iOS模拟器的Debug菜单提供的多款工具可为你提供帮助：

* 减速一个动画来找出问题。

* 触发iCloud同步。

* 辨认出那些可能会有损你应用性能的混合视图层。

* 辨别出源像素没有对准到目标像素的图片

* 查看哪些内容在屏幕外渲染渲染。

* 模拟不同的地点。

![xcode7_15](/images/xcode7_15.png)

在iOS模拟器的任何模拟环境下，主屏幕都会提供打开iOS原生应用（比如Safari，Contacts，Maps和Passbook）的功能。你可以在iOS模拟器中初步的测试你的应用与这些应用的交互。举例来说，如果你正在测试一款游戏，可以使用iOS模拟器来测试这款游戏是否正确调用Game Center。

iOS模拟器中的辅助功能检视器（Accessibility Inspector）可帮助你不受个人制约的测试你应用的可用性。Accessibility Inspector显示你应用可访问的每个元素的信息并且可以模拟VoiceOver与这些元素交互。如果想打开Accessibility Inspector，点击iOS模拟器的主屏按钮然后点击设置>通用>辅助功能。将Accessibility Inspector右侧滑动按钮打开。

你可以在iOS模拟器通过改变语言来测试你应用的本地化。设置>通用>语言与地区>iPhone语言。

尽管你可以在iOS模拟器中测试你应用的基本功能，但是作为一个测试平台，由于诸多原因，模拟器还有很多限制。比如：

* 因为iOS模拟器是在Mac上运行，并使用电脑的内存，这远大于真机上的内存。

* iOS模拟器使用Mac的CPU运行而不是iOS真机的CPU。

* iOS模拟器并不运行真机上的所有线程。

* iOS模拟器无法模拟像加速度计，陀螺仪，摄像头，或者近距离传感器之类的硬件特性。

开发应用时，请务必在你想要支持的所有iOS真机和iOS系统版本上运行和测试。

### 自定义调试工作流 [Customizing Your Workflow](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CustomizingYourWorkflow.html#//apple_ref/doc/uid/TP40010215-CH62-SW1)
***

通过Xcode Behaviors来偏好定制Xcode的行为。选择Xcode> Behaviors，自定义在建立、运行和调试应用时Xcode该做的事。

比如，Xcode可以在你代码在断点暂停时显示调试区域或者在建立应用失败时，显示问题导航器

下面截图中展示了当代码暂停时，Xcode行为是怎么自定义的下面有些自定义行为的例子。

* 每次暂停时播放一个提示音。

* 在工作区域窗体中创建一个名为Debug的标签来展示调试导航器。

* 在Debug标签中同时展示变量视图和控制台视图。

* 在Debug标签中隐藏Utilities区域。

![xcode7_16](/images/xcode7_16.png)

当你设置了上面的行为后，当项目中的代码碰到断点时，Xcode在工作区窗口创建一个debug标签，里面显示特定的内容

![xcode7_17](/images/xcode7_17.png)

你可以自定义Xcode的行为，这些自定义行为可以由菜单中的选项或者绑定的快捷键触发。选择Xcode > Preferences， 选择Behaviors偏好窗口，然后点击底部的Add（+）按钮。输入新行为的自定义名称然后按下Return。在右侧复选框中勾选当你触发这个行为时你想让Xcode做的事。比如，建立一个名为Unit Testing的行为用来保存你工程的快照并且运行你的单元测试。当你建立这个行为后，它会出现在Xcode> Behaviors菜单中。

想给自定义行为添加个快捷键的话，选择Xcode > Preferences然后点击Key Bindings。在Key Bindings偏好窗口中，选择Customized标签找到你自定义的行为。在文本框中，键入快捷键然后点击文本框以外的地方完成操作

## 测试 [Testing](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UnitTesting.html#//apple_ref/doc/uid/TP40010215-CH63-SW1)

***

### 使用单元测试 [Using Unit Tests](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/UnitTesting.html#//apple_ref/doc/uid/TP40010215-CH63-SW1)

***

Xcode支持三种主要测试类型：主要针对代码功能的功能测试，以及测量运行时间的性能测试，以及用户界面的测试。前两种测试都需要你来编写。每种函数都设置了测试环境，对app进行有针对性的测试。

最常用的功能测试是单元测试。代码单元是最小的可测试组件，比如类或者方法集中用来实现基本目的的方法。单元测试通常用来检测代码更改产生的回归。一些开发者首先编写单元测试，然后执行了通过测试的方法。性能测试主要用来衡量app在不同类型设备上完成任务所需的时间。Xcode会根据不同的配置和您选择的基准性能标准来跟踪时间。

测试用例以一个特定方式来运行代码单元或者检测app性能某个特性部分，如果测试结果跟预期结果不同，那么这就是个失败的测试用例。一个测试包由一组测试用例组成。

当你创建项目或者对象（target）时，Xcode会在构建应用程序的scheme中包含一个单元测试对象。对象的实现文件包含setUp、tearDown以及testExample方法的存根。完成这些存根实现，并根据需要为执行应用程序上的单元测试添加其他代码。

通过选择Product > Test来运行所有测试。点击测试导航器图标来查看状态和测试结果。点击测试导航栏右下角的按钮（+）为项目添加测试对象（或者为测试添加类）。想要查看特定测试的源码，请在测试列表中选中，源码编辑器将会打开相应的文件。

![xcode8_1](/images/xcode8_1.png)

想要运行一个测试包，请点击名称右边的箭头。想要运行测试方法的子集，请在测试导航器中选中它，然后选中Product > Perform Action > Run Test Methods。想运行单个测试方法，可点击方法名右边的箭头。选择Product > Test来运行scheme中所有测试。

测试运行成功后，测试名称后边会出现一个带有复选框的绿色菱形。如果测试失败，测试名称右边会出现一个带有X的红色菱形，并且测试中存在的问题会出现在问题导航器中，点击问题导航器按钮即可查看详细问题。

如果仅想查看失败的测试，可点击测试导航器底部的Failed Test按钮（FailedTestIcon）。选中失败的方法便可在源码编辑器中详细查看。解决了造成测试失败的问题后，点击表示失败测试的指示器-带有X的红色菱形-来重新运行测试。

在辅助弹出菜单选中Test Classes 或者Test Callers类别，即可在辅助编辑器中展示相关的测试方法。

### 使用持续集成工作流 [Using Continuous Integration Testing](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/ContinuousIntegrationTesting.html#//apple_ref/doc/uid/TP40010215-CH64-SW1)

***

Xcode通过Xcode service支持持续集成工作流。Xcode service是OS X Server中的服务，可以自动一体化编译、运行单元测试、执行静态分析以及归档产品。Xcode service会报告编译错误和警告、静态分析器问题、以及失败的单元测试。所有测试、分析以及归档都在服务器上执行。

![xcode8_2](/images/xcode8_2.png)

### 使用代码覆盖率 [Using Code Coverage](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/CheckingCodeCoverage.html#//apple_ref/doc/uid/TP40010215-CH74-SW1)

***

Code coverage是一个计算你的单元测试覆盖率的工具。高水平的覆盖给你的单元测试带来信心，也表明你的应用被彻底的测试过了。你可能写了几千个单元测试，但如果覆盖率不高，那么你写的这套测试可能价值也不大。

![xcode8_3](/images/xcode8_3.png)

![xcode8_4](/images/xcode8_4.png)

![xcode8_5](/images/xcode8_5.png)

###  记录UI测试 [Recording UI Tests](https://developer.apple.com/library/mac/documentation/ToolsLanguages/Conceptual/Xcode_Overview/RecordingUITests.html#//apple_ref/doc/uid/TP40010215-CH75-SW1)
***

![xcode8_6](/images/xcode8_6.png)

#### *Recording a Test*

![xcode8_7](/images/xcode8_7.png)

![xcode8_8](/images/xcode8_8.png)
