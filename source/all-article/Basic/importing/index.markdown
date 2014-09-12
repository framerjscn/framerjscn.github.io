---
layout: page
title: "资源导入"
date: 2014-09-04 23:05
comments: true
sharing: true
footer: true
---
<p style="color:#4cb4ec">翻译：亭决 校对：龙抓槐守望者、镇雷 排版：Daniel</p>


### 概述

Framer 生成器可以导入一个打开的 Sketch 或 Photoshop 文件。只有合并成组合（Group）的图层会被导入，而单个图层则会被自动忽略，同时导入后的效果依然遵从原始的图层层级。

修改 Sketch 或 Photoshop 文件后，依然可以方便地重新导入到 Framer。生成器将会自动更新图片以及他们的层级，并且保持你的代码完好。

* 你的层将默认被导入到 myLayers 对象下。
* Framer 允许通过组合名访问图层：myLayers.object。
* Sketch 和 PS 组合中的组合将作为次级层导入。
* Sketch 和 PS 中有矢量元素的组合导入后将自动允许裁剪。
* Sketch 和 PS 中组合的名字必须是唯一的，否则导入时 Framer 将会重命名它们。

只要 Photoshop 或 Sketch 中的图层组没有改名，导入后的所有图层的迭代都会反映到 Framer 中。

### 原则

* 所有 Sketch/Photoshop中的图层组都会成为 Framer 中的一个图层。

{% img /images/target.png %}  

* 图层的层级会被保留，如：子组将变成一个子图层

* 蒙版图层组将变成允许裁剪的图层

{% img /images/masking.png %}  

* 已经被导入的图层importedLayers可用“importedLayers.myLayer”访问

* 组名必须是唯一的

### 要点

* Sketch 或 Photoshop 工程必须保持打开状态才能够导入。

* 在导入文件之前，它至少要保存过一次。

* 所谓图层作为一个平铺式列表导入，因此，调用一个名为“ChildLayer”的图层组应该使用“importedLayers.ChildLayer”而不是“importedLayers.ParentLayers.ChildLayer”。

{% img /images/nesting.png %}  

* 当一个图层组包含其他的组和图层，子图层组将位于所有子图层的最上层。

* 要创建一个可滚动图层，先要确保它包含一个超出它尺寸的图层组。

{% img /images/scrolling.png %}  

* 在Sketch中，所有导入的artboards中只有第一个是默认可见的。

* 在Sketch中，你只能对一个图层组用一个蒙版

* 在Sketch中，确保你导入的文件不要有负坐标，否则它们将在Framer中不可见。

{% img /images/xandy.png %}  

### 兼容性

Sketch 3：兼容但不推荐

Sketch 3.1 Beat：完美兼容

Photoshop CS6：完美兼容

Photoshop CC：完美兼容

Photoshop CC 2014： 完美兼容