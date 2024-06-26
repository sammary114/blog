---
author: Sammary114
author_gh_user: sammary114
tags:
    - scoop
    - package
title: scoop 安装指北
description: 能命令做的事情就不想开浏览器了
---
## 介绍

A command-line installer for Windows

官网地址: [https://scoop.sh](https://scoop.sh)

## 使用理由

> 内容摘自[少数派](https://sspai.com/post/52496)

作为一个包管理器，最基础，也是最重要的功能就是安装软件。正在使用 Windows 的你一定在想：「为什么我要用它？为什么我不直接百度一下？」。

是，你当然可以按照老套路：

1. 百度一下软件名称；
2. 从几十条搜索结果中筛选出那个看起来安全无毒的下载链接；
3. 下载下来一个你不知道有什么捆绑的 exe 可执行文件；
4. 安装到需要管理员权限的目录；
5. 结束。

好麻烦！

Scoop 等一系列包管理器的诞生，第一大便利就是省去了上述繁琐的「搜索 - 下载 - 安装」的步骤，让我们能够通过「一行代码」急速安装。💪

同时，用 Scoop 来安装和管理我们的软件：

- 集搜索、下载、安装、更新软件于一体：极大的降低了安装维护一个软件的成本，我们甚至不必在软件本身的复杂菜单中寻找那个更新按钮来更新软件自己
- 将软件干干净净的安装到电脑的「用户文件夹」下：这样既不会污染路径也不会请求不必要的权限（UAC）
- 在卸载软件的时候，能够尽量清空软件在电脑上存储的任何数据和痕迹

特别的，Scoop 最适合安装那种干净、小巧、开源的软件。并且，Scoop 也极度适合为开发者配置开发环境，不过这些很多都涉及到进阶使用技巧。下面我们先从基础的安装方法开始介绍如何「像 Windows 高手一样管理应用，从 Scoop 开始」。

## 安装方法

### 先决条件

需要执行策略才能安装

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```
