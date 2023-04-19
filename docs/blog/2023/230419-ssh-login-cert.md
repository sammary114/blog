---
author: Sammary114
author_gh_user: zlh953662526
tags:
    - ssh
    - linux
title: ssh 如何使用密钥登录
---

## 前言

为了避免多次使用口令登录的麻烦和键盘监听导致个人使用计算机时出现风险，先记录ssh如何使用证书登录：

该文章要求的知识：

- 知道什么是ssh

- 会linux基础命令

- 会使用搜索引擎查找问题在哪

## 什么是SSH

SSH是一种网络协议，用于计算机之间的加密登录。

## 登录原理

百度

## ssh的登录方法

### 口令登录

默认使用的方法，不想多写

### 证书登录

SSH 密钥登录采用的是非对称加密，每个用户通过自己的密钥登录。其中，私钥必须私密保存，不能泄漏；公钥则是公开的，可以对外发送。它们的关系是，公钥和私钥是一一对应的，每一个私钥都有且仅有一个对应的公钥，反之亦然。

如果数据使用公钥加密，那么只有使用对应的私钥才能解密，其他密钥都不行；反过来，如果使用私钥加密（这个过程一般称为“签名”），也只有使用对应的公钥解密。

> 摘自 [https://cloud.tencent.com/developer/article/1780788](https://cloud.tencent.com/developer/article/1780788)

使用证书登录之前，在客户端使用 `ssh-keygen` 命令生成密钥

```Shell
ssh-keygen -t rsa
```
> 其实原命令是 `ssh-keygen [-t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa]`, 你应该知道`[]`为可选项

第一次生成不懂就一直回车就行，下面介绍每个步骤的解释：

`Enter file in which to save the key (/home/Administrator/.ssh/id_rsa):`

意思为该密钥文件保存的位置

`Enter passphrase (empty for no passphrase):`

为密钥输入密码

之后就会生成 `xx_rsa` 和 `xx_rsa.pub` 两个文件

`xx_rsa` : 私钥，客户端留着

`xx_rsa.pub` : 公钥，服务端留着

（以上说法仅限个人服务使用, 请勿用于公共服务）

**实践部分**

如果提示 `connection refuse` 多半是ssh服务没开或者22端口没有开

如果使用一些支持shell命令的终端（比如`MobaXterm`）可以使用以下命令

```Shell
$ cat ~/.ssh/id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```


如果使用mobaxterm、finalshell等软件, 记得添加私钥文件就行, 不然还是要口令登录

## 省流

个人使用，在你自己的电脑使用`ssh-keygen`生成命令，回车三下，在用户目录的 `.ssh` 目录下，把 `id_rsa.pub` 的内容写入服务器的 `~/.ssh/authorized_keys`的里面就行，如果使用mobaxterm、finalshell等软件, 记得添加私钥文件就行, 不然还是要口令登录



