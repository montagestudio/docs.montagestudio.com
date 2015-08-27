---

layout: docs
title: MontageJS FAQ

prev-page: overlay
this-page: faq
next-page: troubleshooting

---

MontageJS FAQ
=============

以下链接可以查看有关MontageJS常见提问和回复。

* [常见提问](http://docs.montagestudio.com/montagejs/faq.html#general)
* [开始使用](http://docs.montagestudio.com/montagejs/faq.html#gs)
* [授权](http://docs.montagestudio.com/montagejs/faq.html#licensing)

## 常见提问

#### MontageJS是什么？
MontageJS是用标准web最新技术开发的一个开源，客服端MVC应用程序框架。使用MontageJS，开发者可以用已有的HMTL、CSS
和JavaScript技术快速开发单页面应用（SPAs），使用声明式的语法构建用户界面组件，关联DOM，纯页面模板，和CSS样式。

#### 为什么要使用MontageJS？
MontageJS的目标是帮助开发者构建响应式、易维护，能够在不同设备上运行的HTML5 web 应用。可以用框架开发非常简单的单页面web应用，也可以用来构建复杂，庞大，包含很多设计模式，模块分离的企业应用。MontageJS开发可实现：可重用组件，声明式绑定，反应式绑定(FRB)，绘制周期（减少浏览器绘制次数），分割应用功能更好地共享和协作。功能分开能够使设计者只关注页面部分，而不需要去深入了解JavaScript，也能让开发者对组件进行单元测试。

#### 谁正在使用MontageJS?
MontageJS正在快速发展中，但它已经被用于ScratchPad Chrome浏览器扩展应用以及Tips and Tricks 应用（当你第一次打开 Chrome 就可以看到)的开发. 也有很多公司和组织正在他们的项目中使用MontageJS。 虽然当前还没有非常多的例子来说明MontageJS能够做什么，但是你可以先学习它，在学习过程中遇到任何问题可以联系我们。

#### 为什么不能够从官网下载MontageJS?
当前许多框架通过一个链接下载。这样的方式让开发者很容易把框架引入到项目中。 但是其中包含大量项目不需要的功能。 因此，很多web应用在项目中包含大量第三方库，让项目包含了很多冗余功能。

MontageJS使用完全不同的模式开发web应用。使用MontageJS， 你不需要从一个链接下载库，而是在项目开发过程中动态引入。MontageJS使用CommonJS模块系统，它是 npm 包管理系统的一部分。这样使得开发者能够很容易配置开发环境和管理代码。开发阶段把应用需要的功能代码放在不同的模块和组件中。在产品阶段，Mop(MontageJS优化工具) 把应用中引入中MontageJS模块打包到最终的应用中。

## 开始使用

#### MontageJS可以构建什么类型的应用?
MontageJS适合构建单页面 “富客户端”， 在手机，平板电脑，桌面浏览器运行的web应用。当然你也可以用MontageJS构建传统的网页程序，但是这样就不能够使用它提供的强大功能。 例如，查看[示例应用](http://montagejs.org/apps/)。你还可以用MontageJS创建Chrome浏览器扩展和嵌入到WebView里面的本地应用。

#### 如何开始学习MontageJS？
打开[开始使用](http://montagejs.org/docs/montagejs-setup.html)安装开放环境和了解如何在应用中使用MontageJS组件。

#### 整个框架大小？
MontageJS跟传统方式下载然后导入到项目的框架不一样。开发MontageJS应用分为开发阶段和产品阶段，开发阶段编写应用，产品阶段压缩应用。只有在应用中使用到的模块会被打包到最终的应用中。所以框架的大小决定于你的应用使用了多少框架模块。

#### MontageJS支持哪些浏览器?
MontageJS帮助你使用HTML5高级功能来构建富客户端应用，所以不支持过时的浏览器。MontageJS支持最新版本的 Google Chrome，Firefox, Safari, Chrome Android, Mobile Safari, 和 IE 10。

#### 是否支持单元测试?
MontageJS使用[Jasmine specs](https://github.com/montagejs/montage/blob/master/test/core/super-spec.js)做单元测试。可以通过npm方式安装到项目中。安装之后在项目中就有tests.html文件。

可以查看例子[digit](https://github.com/montagejs/digit)了解如何使用单元测试（Digit是用于手持设备的组件库）。 [run-tests](https://github.com/montagejs/digit/blob/master/run-tests.html)页面加载测试环境；script标签中的`data-module="test/all"`设置系统加载test/all.js; all.js定义需要执行测试的模块ids. 注意在这个例子中，所有的测试通过`TestPageLoader.queueTest()`把测试页面加载到iframe中。这样可以保证组件在一个真实的环境里测试，如果同时运行很多测试页面会让浏览器变慢。


我们也使用[mocking their dependencies](https://github.com/montagejs/montage/blob/master/test/base/abstract-button-spec.js)来测试一些组件； 但是现在还不支持单元测试。

#### 能否在Montage应用中访问设备？
Montage只能够使用浏览器支持的设备功能， 所以如果有新的功能被加入到浏览器之后，Montage就可以使用。一旦浏览器有新的设备功能加入，我们很快在Montage中支持。


#### 是否有项目的发布备注和修改日志?

你可以在[发布信息](https://github.com/montagejs/montage/blob/master/CHANGES.md)查看发布信息、修改日志以及已知问题。

### 如何发布bug或者建议?

你可以在MontageJS项目的[GitHub](https://github.com/montagejs/montage/issues)发布bug. 建议或者意见可以在GitHub上创建一个[issue](https://github.com/montagejs/montage/issues)， 可以在[IRC](http://webchat.freenode.net/?channels=montage)加入我们 &#64;montage，可以在 [Google Group](https://groups.google.com/forum/?fromgroups#!forum/montagejs)发布问题。 你也可以在[Twitter](https://twitter.com/montage_js)和 [Google+](https://plus.google.com/116915300739108010954/)找到我们。

## 授权

#### MontageJS是如何授权?
MontageJS是开源项目，遵循[BSD](https://github.com/montagejs/montage/blob/master/LICENSE.md)许可。

#### 是否能够在商业项目中使用MontageJS？是否需要将项目开源?
可以在商业项目中使用，不需要将项目开源。BSD许可允许在应用或者服务中使用框架，而且不需要将项目开源。你也可以把框架源码修改然后二次发布，不需要得到任何许可。

#### 用MontageJS构建的应用是否可以免费？
是的，你可以。
