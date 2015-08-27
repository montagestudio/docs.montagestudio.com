---

layout: docs
title: minit | MontageJS utility

this-page: tools-minit

---

使用minit
========

MontageJS[minit](https://github.com/montagejs/minit)是一个命令行工具，帮助开发者在开发过程中创建种子项目和在本机启动服务器运行项目。`minit`可以创建一个种子项目或文件目录或在一个已有的项目中新建组件。

## `minit`简单例子
在项目目录运行以下命令：

* 创建一个新项目：

		$ minit create:app -n app-name
			
	上面的命令会新建一个`app-name`文件夹，在这个文件夹中包含MontageJS项目默认的目录以及依赖文件。
* 在项目中新建一个组件：

		$ minit create:component -n component-name
		
	上面的命令会在当前项目的ui文件夹中新建一个文件夹`component-name.reel`。里面包含组件的三个文件HTML, CSS,和JS。
* 启动本地服务器，在浏览器中查看项目：

		$ minit serve 
		
	关闭服务器使用快捷键`Ctrl C`，如果要让服务器在后台运行在末尾添加 & 参数：`minit serve &`;
* 获取`minit`的最新版本：

		$ npm install -g minit@latest
		
* 查看minit命令行的全部参数：

		$ minit --help
		
在[minit repo on Github](https://github.com/montagejs/minit)上查看更多介绍。