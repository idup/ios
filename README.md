# ios-app 使用说明

## 环境准备

[ios-app 网站](http://ios-app.idup.club)由[hexo](http://hexo.io) 生成，请使用`npm install hexo-cli -g`命令安装hexo环境（npm的安装可使用brew，brew的安装请自行解决）

## 从github获取既有代码

`git clone https://github.com/idup/ios-app`

## 安装ios-app hexo工程依赖包

`cd ios-app`

`npm install`

## 添加、修改内容

使用`hexo new "article title"` 创建新文章或编辑source\\\_posts\目录下已有md文件修改既有文章内容

## 发布内容

使用`hexo generate` 命令重新生成网页内容，并使用`hexo deploy`命令发布生产的内容到网站。

## 提交更新内容

按git流程提交对ios-app的hexo内容所做修改（`git add .` -> `git commit -a` -> `git push origin master`），在此之前，当然你需要授权，请联系 [admin@idup.club](mailto:admin@idup.club)。
