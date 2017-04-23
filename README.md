## 网站性能优化项目

你要做的是尽可能优化这个在线项目的速度。注意，请应用你之前在[网站性能优化课程](https://cn.udacity.com/course/website-performance-optimization--ud884/)中学习的技术来优化关键渲染路径并使这个页面尽可能快的渲染。

开始前，请导出这个代码库并检查代码。

### 指南

####Part 1: 优化 index.html 的 PageSpeed Insights 得分

以下是几个帮助你顺利开始本项目的提示：

1. 将这个代码库导出
2. 你可以运行一个本地服务器，以便在你的手机上检查这个站点

```bash
  $> cd /你的工程目录
  $> python -m SimpleHTTPServer 8080
```

1. 打开浏览器，访问 localhost:8080
2. 下载 [ngrok](https://ngrok.com/) 并将其安装在你的工程根目录下，让你的本地服务器能够被远程访问。

``` bash
  $> cd /你的工程目录
  $> ./ngrok http 8080
```

1. 复制ngrok提供给你的公共URL，然后尝试通过PageSpeed Insights访问它吧！可选阅读：[更多关于整合ngrok、Grunt和PageSpeed的信息](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)。

接下来，你可以一遍又一遍的进行配置、优化、检测了！祝你好运！

----

####Part 2: 优化 pizza.html 的 FPS（每秒帧数）

你需要编辑 views/js/main.js 来优化 views/pizza.html，直到这个网页的 FPS 达到或超过 60fps。你会在 main.js 中找到一些对此有帮助的注释。

你可以在 Chrome 开发者工具帮助中找到关于 FPS 计数器和 HUD 显示的有用信息。[Chrome 开发者工具帮助](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### 一些关于优化的提示与诀窍
* [web 性能优化](https://developers.google.com/web/fundamentals/performance/ "web 性能")
* [分析关键渲染路径](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "分析关键渲染路径")
* [优化关键渲染路径](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "优化关键渲染路径！")
* [避免 CSS 渲染阻塞](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "css渲染阻塞")
* [优化 JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [通过 Navigation Timing 进行检测](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api")。在前两个课程中我们没有学习 Navigation Timing API，但它对于自动分析页面性能是一个非常有用的工具。我强烈推荐你阅读它。
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">下载量越少，性能越好</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">减少文本的大小</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">优化图片</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP缓存</a>

### 使用 Bootstrap 并定制样式
这个项目基于 Twitter 旗下的 <a href="http://getbootstrap.com/">Bootstrap框架</a> 制作。所有的定制样式都在项目代码库的 `dist/css/portfolio.css` 中。

* <a href="http://getbootstrap.com/css/">Bootstrap CSS</a>
* <a href="http://getbootstrap.com/components/">Bootstrap组件</a>

## 如何运行本应用
本项目未使用构建工具，将这个库下载到本地然后用浏览器打开index.html即可运行，或者，你也可以访问本项目的 [GitHub Pages](https://huangziyu.github.io/WebsiteOptimization_zh/) 来运行。

## 对 index.html 进行的优化概述
* 将 print.css和Google Fonts css变为异步加载，通过添加 media:print 属性 和[ Web Font Loader ](https://www.lockedowndesign.com/load-google-fonts-asynchronously-for-page-speed/)来实现。
* 将 style.css 嵌入 index.html 以缩短关键渲染路径长度。
* 对 index.html 中引用的图片进行了压缩。

最终[Google PageSpeed Insights 评分](https://developers.google.com/speed/pagespeed/insights/?url=https%3A%2F%2Fhuangziyu.github.io%2FWebsiteOptimization_zh%2F&tab=desktop)为 94 移动设备/96 桌面设备。

## 对 pizza.html 的 FPS （每秒帧数）进行的优化概述
* 参考[避免强制同步布局](https://developers.google.com/web/fundamentals/performance/rendering/avoid-large-complex-layouts-and-layout-thrashing#_2)对 changePizzaSizes 函数进行了重构，先读取样式而后执行更改以避免强制同步布局问题。
* 使用 requestAnimationFrame 优化 updatePositions 中的绘制动画操作。
* 为披萨滑窗增加了 will-change CSS 属性，这样每一个 pizza 都会有自己的图层，可以避免图层重绘制。
* 最终在 Chrome 开发工具的 Rendering-FPS Meter 中滚动页面可以看到fps稳定在60。

## 两个优化结果的截图
![Google PageSpeed Insights 评分](https://github.com/huangziyu/WebsiteOptimization_zh/blob/master/imgforreview/pagespeedinsight.png)
![FPS Meter](https://github.com/huangziyu/WebsiteOptimization_zh/blob/master/imgforreview/fps.png)
