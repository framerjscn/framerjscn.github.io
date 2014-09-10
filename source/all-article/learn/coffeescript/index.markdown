---
layout: page
title: "CoffeeScript 简明教程"
date: 2014-09-04 23:05
comments: true
sharing: false
footer: false
---
<p style="color:#4cb4ec">翻译：镇雷 校对：龙抓槐守望者 排版：Daniel</p>


本节内容主要介绍 CoffeeScript 的基本语法，或者当做备忘录来使用。通过以下内容，不仅专注于 Framer Studio 的设计师，其他任何想要学习 CoffeeScript 的人都可以在段时间内掌握这门语言。

**值得学习 CoffeeScript 的理由：**

* 简介易读的语法，容易学习和上手。

* 帮助开发者避开 Javascript 的困难部分。

* 可使用快捷键进行高效工作。

##基本语法

###注释

注释使用前缀#来表示这不是实际的代码，开发者通常使用注释以说明附近代码的具体功能。

	# I am a comment
	5 + 6 # I am a comment too

###打印与输出

开发者可以通过将变量打印出来以检验代码的正确性。


	console.log "Hello" # Output: Hello
	console.log "Hello", "World" # Output: Hello World

###空格

CoffeeScript 对空格和 Tab 是敏感的，它们被用来代替 Javascript 中的 { 和 } ，这意味着如果代码中的空格和 tab 不正确，程序将会出错。

	if 1 + 1 == 2
	    console.log "hello" # This will work

	if 1 + 1 == 2
	console.log "hello" # This will fail (missing tab)

###变量

变量是一个带有名称的容器，用来存储数据和信息，它的用法非常简单：

	myVariable = 1

上述例子中的变量 myVariable 中包含了数据 1，开发者也可以为其分配任意的其他值。

倘若一个变量没有赋值，则其会返回一个特殊值 ’undefined’ ，因此当程序报错 undefined 时，很有可能是开发者正在使用一个实际还不存在（未赋值）的变量。

通过后面的内容，我们将看到变量可以存储各种不同类型的数据。


##数据类型

###布尔型数据

每一个布尔型数据只有两种值：false 或 true：
	
	myBoolA = true
	myBoolB = false

###数

数可以是整数、小数等，当然还包括正数和负数。

	myNumberA = 2
	myNumberB = 20.0
	myNumberC = -223894

数可以直接进行各种运算，比如：

	myNumberA + myNumberB  # Add, output: 22.0
	myNumberA / myNumberB  # Divide, output: 0.10
	myNumberA * myNumberB  # Product, output: 40.0
	myNumberA ** myNumberB # Power, output: 400.0

###字符串

字符串是一系列字母的集合，它可以是一个单词，也可以是一个完整的句子：

	myStringA = "Hello there”

开发者可以将字符串进行组合：

	myStringB = "#{myStringA}, I am the dude"
	# Output: "Hello there, I am the dude"

字符串还存放许多通过数没法表达的数据：

	myStringC = "rgba(255,0,0,0.1)"
	myStringD = "1px solid #FFFFFF”

###数组

数组用于存放一系列有顺序的数据（支持各种数据类型），与其他语言一样，CoffeeScript 也支持多维数组（即由数组组成的数组）。

	myListA = [1, 2, 3, 4, 5] # Just numbers
	myListB = [1, "test", 22, [1, 2, 3]] # Mixed

开发者可以通过编号（索引）来定位数组中的任一数据，编号从 0 开始。

	myListA[0] # Output: 1
	myListA[4] # Output: 5

开发者也可以通过自带的函数统计数组的长度：

	myListB.length # Output: 4

或者获取某一编号范围内的数据：
	myListB[0..2] # Output: [1, 2, 3]


###对象

对象与列表有些类似，区别则在于除了通过编号索引以外，对象还可以通过字符串来进行索引。（译者注：键值对）

	myObjectA = {name:"Framer", age:12}

也可以通过下面的方式来创建对象，这和上述方法是等效的：

	myObjectA =
	    name: "Framer"
	    age: 12

通过关键词索引数据：

	myObjectB["name"] # Output: “Framer"

如果所使用的关键词不存在，则会返回 undefined：

	myObjectB["nothere"] # Output: undefined

一旦开发者创建了一个对象，也可以为其增添新的内容：

	myObjectB["platform"] = “Mac"

当然你也可以移除一些内容：

	delete myObjectB["platform"]
	myObjectB["platform"] # Output: undefined


##函数

函数是一整块的可执行代码，顾名思义，它的功能和数学中的函数非常类似——接收输入，产生输出。函数的运行称为『调用』，而函数的输入称为『参数』。

什么情况下我们需要使用函数：

1.描述一个任务，但是只在需要的时候调用它
2.将那些不断重复的工作归入一个函数中，方便开发者对其反复调用

下面的例子介绍了如何定义一个函数，其方式与定义变量非常类似。关键词 return 将一个值传给函数的调用者（默认情况下，CoffeeScript 将返回最后一个被使用的变量）。

	myFunction = (input) -> 
	    output = input * 2
	    return output

调用函数，并且将 42 作为参数传入：

	myFunction(42) # Output: 84

开发者还可以将函数的输出直接赋值给一个新的变量：

	myCalculatedNumber = myFunction(42)
	myCalculatedNumber # Output: 84

当然，函数可以定义一些列不同类型的参数：

	myFunction = (argumentA, argumentB, argumentC) ->
    	return argumentA + argumentB + argumentC

###比较器

比较器用来比较数据，如常用的等于、大于、小于等。

	4 is 4 # Output: true
	4 isnt 4 # Output: false
	4 < 5 # Output true
	4 > 5 # Output false

开发者可以使用 or 或者 and 来组合比较器：

	4 is 4 and 5 < 4 # Output false
	4 is 4 or 5 < 4 # Output true

###条件语句

条件语句结合比较器，可以用以定义程序逻辑。条件语句的关键词有 if，else if，和 else。

	if age > 21
	    console.log "Over 21!”

再来看一个稍复杂一些的例子：

	if age < 21
	    console.log "Young"
	else if age < 65
	    console.log "Adult"
	else
	    console.log “Senior"

###循环语句

循环语句用来进行程序中的重复计算，循环体可以是数组或对象。循环关键字为 for。

关于数组循环的例子：

	myArray = [1, 2, 3, 4, 5]

	for number in myArray
	    number + 1

	# Output: 2, 3, 4, 5, 6
一个含有键值对的对象也可以纳入到循环中来，将关键字 in 改为 of 即可：

	myObject =
	    name: "Koen"
	    city: "Amsterdam"
	    age: 31

	for key, value of myObject
	    key, "=", value 

	# Output: name=Koen, city=Amsterdam, age=31

##常见错误

SyntaxError … unexpected …：编译器遇到一段用途不明的代码（一般可能是语法错误）。

ReferenceError … Can’t find variable …：你正在使用一个编译器不能识别的变量，可能是对其申明有误。

##更多 CoffeeScript 资源

推荐一些优质的站点，帮助那些希望在 CoffeeScript 上走的更远的设计师和开发者：

* [Convert any Javascript to CoffeeScript](http://js2coffee.org "Title")
* [The official CoffeeScript Site](http://coffeescript.org/ "Title")
* [The Little Book on CoffeeScript](http://arcturo.github.io/library/coffeescript "Title")
* [Code School CoffeeScript Course](http://coffeescript.codeschool.com/ "Title")(Paid)