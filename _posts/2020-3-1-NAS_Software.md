---
layout: post
author: Bob Guo
title: 垃圾佬的家庭网络中心 （2）
subtitle: 软件篇
date: 2020-3-1
tags: 网络 NAS
published: true
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先，先说几个硬件方面的变更。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我放弃了E3-1220LV3，而是继续使用现有的G1840.经过跟这方面的一些人士探讨之后,由于H81平台本身的限制，我不认为继续购入一颗2c4t的处理器来提供超线程是一个具有高性价比的选项-尤其是我并不打算长期使用这套平台承载大量专业需求的情况下。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我购入了一张网卡，具体型号是英特尔的i340,也算是一代经典了，老当益壮，富士通的卡。说来我之前还玩过一个富士康的Q77主机，虽然下场特别凄惨-你敢相信这玩意儿连特么的UEFI都不支持吗？最离谱的是富士康是UEFI联盟的成员，旗下旗舰级商务产品线竟然没有UEFI，你听人言否？至于无线AP，虽然不用但我正好手上有一个闲置的Intel AC 7265无线网卡，我就把它插上去了。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;至于内存和固态，很幸运我还能找到几台DDR3的机器，从上面又拆了一根4GB的条子下来。运气很好的是，即使使用的内存在规格上与现有的内存n相差甚大，我仍然成功点亮机器。而CPU的钱则被我用来购入了一块三星的128G固态硬盘。150的高价，不用说，ng这显然不是极高性价比的方案。但是，基于SATA的存储方案相比于我之前基于USB3总线的存储方案在磁盘IOPS和速度上都胜过一头，也对各种操作系统有更好的支持。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后是软件。软件方面，我暂时放弃专用Linux发行版方案。不只是因为Linux下的网络调教对我来说na难度太大，或者借用京都动画撤下山本宽的名言：まだ、その域に达していない判断し。Windows下Hyper-V方案对我来说可能更为易用，且我也确实需要一个能稳定的Windows设备。目前来讲我已经成功安装windows 10、Hyper-V以及在Hyper-V里面成功部署了一套OpenWRT的虚拟机。并且，我也成功进入了控制界面。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然而令人痛苦的事情还在后面。进入OpenWRT的控制界面远远不是万事大吉。基本的配置工作仍然还无法完成，连续三天苦战后我已经决定暂时放弃这个项目，先让设备吃几天灰，之后在回去处理它。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;结果过了几天，本来可以正常工作的OpenWRT又无法正常工作了，而WIndows 下的网络h部署比Linux还要磨人，我已经习惯Linux万物皆文件 的设计哲学，再为了这点东西浪费时间学Windows不仅有法律和道德风险还浪费时间精力。Ubuntu 18.04请。