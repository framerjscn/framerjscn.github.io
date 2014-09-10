---
layout: page
title: "镜像（Mirror）"
date: 2014-09-07 23:05
comments: true
sharing: true
footer: true
---
<p style="color:#4cb4ec">翻译：镇雷 校对：龙抓槐守望者 排版：Daniel</p>

### 概述

Mirror 功能主要用于在移动设备上预览原型。设备要求与 Mac 处于同一 WiFi 环境，并且使用基于 WebKit 的浏览器，包括：iPhones、iPads、Android 和其他平板设备。当在 Framer 中保存文件，所有设备上预览的项目都会同步刷新，这让实时原型浏览更加便捷。

通过右上角工具栏中的 Mirror 按钮即可看到底部的 URL，在移动设备浏览器中打开这个链接即可使用 Mirror 功能。你还可以使用分享、消息与 email 功能快速发送链接到其他设备。

{% img /images/toolbar.png %} 

Framer Studio 目前将所有打开的工程都运行在一个内建的 web 服务器上，其地址主要基于你目前的网络 IP 地址，形如10.0.1.123:8000/YourProject.framer。因为这是标准的 web 服务器，不依赖于 Bonjour，因此其应当能够运行在所有网络中，包括企业管理网络。

想要查看所有正打开的项目，访问 web 服务器的根目录即可,只要点击相应的项目就可以进入预览了。

{% img /images/projects.png %} 

### iOS 设备

* 长按分享按钮，选择"Add to Home Screen"可以将项目添加到主屏，我们还专门为你的项目设计了一枚默认图标。

* 想要体验真正全屏的原型预览,可以使用 [FSMirror]("http://framerjs.com/learn.html#importing") 插件。iOS 的一些特定标签如 minimal-ui 和 apple-mobile-web-capable 可能无法正常使用。

### 其他设备

* 初始缩放比例 [meta 标签]("https://developer.mozilla.org/en/docs/Mozilla/Mobile/Viewport_meta_tag") 默认为0.5，当在 Retina(@2x)设备上运行是效果最佳，当需要运行在 @1x 的设备上时，需要修改比例值。

* 如果希望将原型以离线的形式保存和浏览，可以在 URL 中增加/offlin.html，这可以使用 HTML5的离线缓存。注意离线形式无法自动刷新。

### 要点

* 切换网络或网络设置时，需要重启 Framer Studio。

* 如果网络状况不佳，可以通过 [tethering trick]("http://bjango.com/help/skalapreview/connection/") 来使用USB 代替 WiFi 链接。

* 如果 Framer Studio 无法通过8000端口访问，尝试使用其他可用端口（8001，8002等）

* minimal-ui viewport 标签在 iOS8中无法使用，因此它默认是不可用的。

* apple-mobile-vweb-app-capable 标签目前存在一些 bug，也许会导致手机卡死，因此它也是默认不可用的，也许这个问题在 iOS8中会修复。

### 故障检查

如果你的设备不能找到网络中的服务器：

1. 确认是否设备与 Mac 处于同一网络中 

2. 尝试使用本地 DNS 来代替 IP 地址，具体可以在 System Preferences > Sharing 中查看，它应该形如：my-computer.local:8000/MyProject.framer

3. 查看网络的防火墙是否阻断了8000-9000端口。