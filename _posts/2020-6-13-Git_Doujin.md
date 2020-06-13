---
layout: post
author: Bob Guo
title: 用技术手段保障你的同人创作
subtitle: 利用Git维护你和你社区的同人创作作品
date: 2020-6-13
tags: 同人 数据备份 Git
published: false #write true to publish this article.
---
# DISCLAMER
*本文章所有内容仅供抛砖引玉，在实际操作中请确认你的行为并不违反你所在国家、地区的法律。如果你有需要，本文章将以[CC-BY-SA-NC 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)协议共享。*
# DISCLAMER OVER
## 0x01 What Happened?
如果你正在看这篇文章，我相信你已经对从公元2020年2月27日开始的一系列网络冲突有所耳闻。如果你不清楚，[这里](https://zh.wikipedia.org/wiki/%E8%82%96%E6%88%98%E7%B2%89%E4%B8%9D%E4%B8%BE%E6%8A%A5%E4%BA%8B%E4%BB%B6)是事件的维基百科页面，你可以去阅读一下对目前的事态略知一二。简而言之，饭圈内讧导致AO3被墙，节奏爆发至今。  
在昨天（2020年6月12日），网易运营的中文内容创作平台Lofter由于涉黄被下架，在此之前该网站内部出现大量机器人发送色情图片和链接，被怀疑仍然是肖战粉丝所为。由于各个渠道传来的消息都极为悲观，作为同人创作社群的一份子，我觉得我有必要站出来提供一个我的解决方式-基于Git的分布式版本管理方案。
## 0x10 Why Git?
看这篇文章的不一定有专业程序员和CS爱好者，所以在此之前，我们先要理清两个概念：Git和分布式版本管理。首先，借用一下维基百科的[解释](https://zh.wikipedia.org/wiki/%E5%88%86%E6%95%A3%E5%BC%8F%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)，在程式设计中，分散式版本控制（英语：distributed revision control 或 distributed version control，又译为分布式版本控制），又称去中心化版本控制（decentralized version control），是一种版本控制的方式，它允许软件开发者可以共同参与一个软件开发专案，但是不必在相同的网络系统下工作。以分散式版本控制方法，作出的软件版本控制系统，称为分散式版本控制系统（distributed revision control system，缩写为DRCS，或是distributed version control system，缩写为DVCS）。简单来说，分布式版本管理可以做到人在塔在，无论是AO3还是Lofter倒了都没关系，只要还有一个人在本地存有这个文章，文章就不会丢失。而且，版本管理软件会对所有修改做记录，尤其是配合[GnuPG](https://zh.wikipedia.org/wiki/GnuPG)等密码学软件对修改用电子签名记录后，一旦涉及版权争端将会成为保护合法权益的非常有力的武器。而Git，就是众多分布式版本管理软件中的佼佼者。它由大名鼎鼎的[Linus Torvalds](https://zh.wikipedia.org/wiki/%E6%9E%97%E7%BA%B3%E6%96%AF%C2%B7%E6%89%98%E7%93%A6%E5%85%B9)开发，是目前最广泛使用的分布式版本管理软件之一。上到Linux内核和Android Open Source Project，下到大学生CS50作业，Git都可以管理。而对于大多数同人创作的图片和文字来说，利用Git来管理可谓再好不过了。而且，有很多网站可以提供免费的Git项目托管，例如[GitHub](https://github.com/)、[GitLab](https://about.gitlab.com/)和[码云](https://gitee.com/)。无论是这三家的哪一家都可以免费为你部署一个静态页面，而为了方面我们这里就选择使用码云。当然，如果你对任何一家服务不爽了，你可以很快把你的项目迁移到另一家平台上。
## 0x11 How to start?
首先，在开始之前，在你的本地电脑上安装Git。从[这里](https://git-scm.com/)