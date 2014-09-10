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
The importer lets you import Sketch or Photoshop documents directly into Framer. 
你可以直接导入Sketch或者Photoshop的文件到Framer，

Framer允许直接从 Sketch 或 Photoshop 中导入素材，所有图层组都能够被调用，并且图层层级保持原状。

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