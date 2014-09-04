---
layout: post
title: "安装 Framer.JS"
date: 2014-09-03 16:27:32 +0800
comments: true
categories: 教程
---

一切，从下载 Framer 开始。

打开 index.html 文件可以查看默认原型——一个随点击弹性跳动的 Logo。想要为原型增加交互或者动画，可以在代码编辑器中编辑 app.js，来试试给 imageLayer 这个层添加一个状态吧：

	fifth: { y:200, scale:0.8, rotationZ:200, blur:2 }

imageLayer 层将在第四次点击的时候产生移动、旋转及布尔运算效果。

注意：Framer在 WebKit 引擎下效果最佳，所以官方推荐使用 Safari 浏览器。Chrome 等浏览器也可以运行，但由于 Blink 引擎的关系，有些效果显示并不完美。