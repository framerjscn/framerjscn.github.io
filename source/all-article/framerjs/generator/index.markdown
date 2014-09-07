---
layout: page
title: "生成器"
date: 2014-09-04 22:56
comments: true
sharing: true
footer: true
---
翻译：镇雷 校对：龙抓槐守望者

Framer 生成器可以导入一个打开的 Sketch 或 Photoshop 文件。只有合并成组合（Group）的图层会被导入，而单个图层则会被自动忽略，同时导入后的效果依然遵从原始的图层层级。

修改 Sketch 或 Photoshop 文件后，依然可以方便地重新导入到 Framer。生成器将会自动更新图片以及他们的层级，并且保持你的代码完好。

* 你的层将默认被导入到 myLayers 对象下。
* Framer 允许通过组合名访问图层：myLayers.object。
* Sketch 和 PS 组合中的组合将作为次级层导入。
* Sketch 和 PS 中有矢量元素的组合导入后将自动允许裁剪。
* Sketch 和 PS 中组合的名字必须是唯一的，否则导入时 Framer 将会重命名它们。