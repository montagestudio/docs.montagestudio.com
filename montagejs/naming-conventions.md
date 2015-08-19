---
layout: docs
title: Naming Conventions
this-page: naming-conventions
redirect_from: /docs/Naming-Conventions.html
---

命名规范
=======
这个文档总结MontageJS命名规范以及如何在模块、组件和CSS类名中使用。在构建应用或者提交代码到MontageJS框架时需要遵循这些规范。

##模块
模块名由小写字母和数字组成，可以用中横线分割（如，`child-package`）；

##组件（.reel文件夹）
组件存放在MontageJS项目的ui文件夹中，组件对应的文件夹名以.reel结尾。

`.reel`文件夹名需要符合以下命名规范：

* 组件名是小写字母。
* 可以用中横杠分割单词。例如：`radio-button.reel`，`text-field.reel`。

##CSS类名
CSS类名遵循中横杠分割规范：`package-Component`，`package-Component-childElement`。 类型和状态相关的样式使用双横杠。比如下面的Digit Progress组件：

	.digit-Progress          /* package-Component */
	.digit-Progress-bar      /* package-Component-childElement */
	.digit-Progress--small   /* package-Component--variation */
	.digit-Progress--loading /* package-Component--state */
	
更多规范：

* __组件:__ CSS类命由包名(例如，`montage-`, `digit-`, `matte-`等等)+中横杠然后组件名首字母大写；例如一个按钮组件的CSS类名就是`digit-Button`:

		<button class="digit-Button">
		
	如果组件名是由多个单词组成，每个单词的首字母都需要大写。例如，`montage-InputRange。
* `复合组建:` 组建中的子元素遵循以下规范：
	* 如果一个组件有子元素，子元素名小写（用来区分父组件还是子组件），父元素与子元素用中横杠分割；例如,`digit-Slider-thumb`。
	* 如果子元素名由多个单词组成，子元素名用小写驼峰规则;例如，digit-Slider-thumbWithSpikyEars`。
	* 如果子元素多层次的，每一层用中横杠分割；例如，`digit-Slider-thumb-nobs-centerNob`（_注意:_ 一般不建议这样做，因为这样会让类名很长。只有在真正需要的时候使用。)）
	
		>__备注:__ 从技术上是没有限制子元素层次数量，但是如果有很多层次的时候应该把子元素封装成单独的组建。
		
* __类型:__ 如果组件有几种类型，用双横杠风格。例如： `digit-Button--primary`, `digit-Slider--vertical`。
* __状态:__ 如果组件有几种状态，用`is-`前缀；例如：`is-hidden`, `is-active`。 这是为了说明组件有几种不同的状态，不应该全局设定。由组件内部控制：`.Component.is-hidden { display: none; }`。

##理论基础
MontageJS CSS命名规范借鉴[BEM](http://bem.info/method/)方法论，然后在语法上做了一些小调整:

* 在名字中包含包名是为了在应用中的多个包互相不冲突。
* 使用中横杠（ - ）是为了在编写代码的时候能够双击一部分就能够全选然后编辑。（你可以试一下 `digit-Slider-thumb` 和 `digit_Slider_thumb`）
* 组件名大写驼峰格式是为了区分组件/子组件之间的关系。
* 子元素小写驼峰格式是为了增加可读性，同时也保证每个部分分组在一起。