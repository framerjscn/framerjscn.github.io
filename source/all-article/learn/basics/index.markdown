---
layout: page
title: "Framer.JS基础"
date: 2014-09-04 23:04
comments: true
sharing: true
footer: true
---
_翻译: 亭决 校对：龙爪槐守望者、镇雷_
***

本节主要通过一些具体的例子介绍 Framer 的基本使用方法以及核心设计原则。下述的所有程序都是用 CoffeeScript 编写的，但大部分在 JavaScript 规则下也同样适用。

##Framer.JS 基础知识

### 图层 Layers

图层通常用于绘制或承载浏览器中的界面元素，其默认形状为矩形。 
图层除了 x, y 坐标、长度、宽度这些基本属性外，还可以修改其透明度、缩放比例、布尔运算等高级设置。

	# This creates a new layer, and sets its x property to 100
	myLayer = new Layer({x:0, y:0, width:128, height:128})
	myLayer.x = 100

### 层级 Layers

Layers can contain other layers. We call these subLayers.
图层中所包含嵌套的其他图层称为子图层（SubLayers），子图层继承自父图层。当然，设计师也可以根据需要调整图层之间的层级关系。
比如：如果你将父图层的的透明度变为0.5，其他所有子图层的透明度都将有被设置为透明度0.5。
一个图层的坐标基于它的父图层，也就是说如果一个图层的x，y坐标都是0，它的位置将在父图层的左上角。

	# Adds a subLayer to a layer
	parentLayer.addSubLayer(childLayer)

### 图像和滚动 Images And Scrolling

大多数的图层只包含一张图片，并且设置图片的属性非常简单。

	# Set an image
	layer = new Layer({width:100, height:100, image:"my-image.png"})

另外，图层中的内容可以通过设置『scroll』关键字来设置其是否允许滚动。

	# Make layer scrollable
	layer = new Layer({width:100, height:100})
	layer.scroll = true

当诸多图层被组合到一起时，称为视图（View），也可以成为 Widgets 或 Components，比如 iOS 中的 TableView、CollectionView等。视图往往被用于不同工程之间的复用。

### 动画 Animation

绝大部分图层的属性都可以设置动画效果。通过设置曲线（curve）能够定义不同的动画类型，比如'linear'（线性）、'ease-in'（缓进）、'spring'（弹性）等。

你可以通过如：myAnimation = layer.animate({..})或layer.animate({..})来准确定义一个动画。

	# Creates an animation using a spring
	springUp = layer.animate({
    	properties: {y: layer.y + 100},
    	curve: "spring(100,10,0)",
	})

### 样式 Styling
Because Framer runs in the browser, you can simply use html and css to style any layer. 
Framer运行在浏览器中，因此可以很容易地使用html和css规定图层和样式，如通过 somelayer.html = "hello" 来设置图层的 html 内容。
而通过编辑图层属性参数，相当于添加 css 样式：layer.style.backgroundColor = "red" or layer.style['background-color'] = "red", 或者像后面的例子一样，一次性修改不同的参数。

值得注意的是，与大多数使用数值作为变量内容的 Framer 属性不同，样式需要明确的 css 变量内容来指定：layer.style.lineHeight = "16px"。你还可以通过如 layer.classList.add("myClass")来为图层设置一个 css 类，以便从外部引入 css 样式文件。

	# Set multiple layer styles at once
	layer.style = {
    	"font-size": "18px",
    	"text-align": "center",
    	"line-height": "24px",
    	"color": "red"
	}

注意：如果你在图层上设定单个样式，别忘了用javascript语法，如：’font-size’应该是layer.fontSize

### 事件 Events

事件可以作用于图层，如用户点击、鼠标悬停，或者是滚动。你可以设置监听这些动作的发生来创建简单或复杂的交互。 

Framer 提供了很多可以监听的时间，最常用也是最有意思的有点击、双击、鼠标悬停、鼠标离开和键盘按键等。而移动浏览器上的特殊触摸事件有：触摸开始，触摸移动，触摸结束。
Framer能帮助智能地定义常见的动作，如’Events.TouchStart’将在PC上被视为鼠标按下，在移动端则是触摸的开始。

监听一个事件可以使用 layer.on event,->…，停止则用 layer.off event,->…，允许同时定义多个事件。

	# Listen to multiple events on a layer
	layer.on Events.TouchStart, (event) ->
    	console.log "Touch/click start happened on layer"
	
	layer.on Events.TouchMove, (event) ->
    	console.log "Touch/click is moving!"
	
	layer.on Events.TouchEnd, (event) ->
    	console.log "The touch has ended :("

值得注意的是，函数中的 event 是一个关于事件触发的对象，它携带事件的附加信息。

### 状态机 State Machine
状态机是Framer3中的一个新特性，强大且实用。它允许你为图层叠加多个『状态』——可以理解为图层的参数设置。一个图层也可以有多个状态，你能添加或删除它们，可以在状态间切换或定义动画，也可以随时切换图层的任意一个状态。一个图层所有的状态可以拥有一个共同的动画属性，如曲线动画效果。图层将会有一个“默认”状态，这也是图层在创建时的就设置好的参数。

在图层要被呈现在屏幕上时，除了位置、尺寸等参数以外，状态可以说是最有用的。
举个例子，我们用状态机来为一个图层添加三个状态，再赋予点击时每个状态之间切换动画。
 
 # Add three states to the layer
imageLayer.states.add
    tooSmall:  {scale: 0.8}
    tooBig:    {scale: 1.2}
    justRight: {scale: 1.0}

	# Set the default animation options for the layer
	imageLayer.states.animationOptions =
    	curve: "spring(200,12,10)"
	
	# On a click, go to the next state
	imageLayer.on Events.Click, (event) ->
    	imageLayer.states.next()
