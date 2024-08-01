---
author: Sammary114
author_gh_user: sammary114
tags:
    - windows 10
    - usb
    - error
    - code19
title: 关于 windows 设备管理器提示错误 “代码19” 的解决办法
description: 评价是太闲写的教程
---

## 起因

来自一名小米13用户的帮助, 本人自信的以为是 windows 10 日常 usb 驱动抽风，自己手动更新就好（没认真看错误导致的）

## 经过

对方自己更新还是解决不了问题，自己远程上手，手动更新驱动，才发现错误 “代码19”，网上资料查了半天没有一个正经的。不过好在youtube和联想的笔记本解决方案提供了参考（但是内容都不沾边）

[联想提供的解决方案](https://iknow.lenovo.com.cn/detail/183006)

[油管视频](https://www.youtube.com/watch?v=7wAQYTKc19Y&themeRefresh=1)

所以上面两个内容有一定的误导性，下面具体写下

## 正确操作

1. 在设备管理器找到`代码19`的设备, 如图：
2. 双击打开，弹出设备属性页面，提示注册表错误
3. 在属性页中，点击标签页的详细事件，在属性列表中选择`类guid`，记住对应值
4. 按`WIN+R`组合键打开运行，输入`regedit`后回车，打开注册表
5. 找到`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class{对应guid值}`项
6. 打开UpperFilters，删除其中数据，点击确定
7. 操作完成后，重启即可恢复正常
