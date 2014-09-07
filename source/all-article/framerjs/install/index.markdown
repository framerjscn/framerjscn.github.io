---
layout: page
title: "安装"
date: 2014-09-04 22:38
comments: true
sharing: true
footer: true
---
<p style="color:red">翻译：镇雷 校对：龙抓槐守望者 排版：小和</p>


一切，从下载 Framer 开始。

打开 index.html 文件可以查看默认原型——一个随点击弹性跳动的 Logo。想要为原型增加交互或者动画，可以在代码编辑器中编辑 app.js，来试试给 imageLayer 这个层添加一个状态吧：

	fifth: { y:200, scale:0.8, rotationZ:200, blur:2 }

imageLayer 层将在第四次点击的时候产生移动、旋转及布尔运算效果。

注意：Framer在 WebKit 引擎下效果最佳，所以官方推荐使用 Safari 浏览器。Chrome 等浏览器也可以运行，但由于 Blink 引擎的关系，有些效果显示并不完美。