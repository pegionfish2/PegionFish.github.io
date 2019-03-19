---
layout: post
title: Hackintosh To Go
subtitle: 将macOS High Sierra开发环境迁移到移动U盘中
tags: 
    -黑苹果
    -Hackintosh
    -macOS
published: true
---

众所周知，作为一个C程序员兼Linux爱好者，我对GNU/Linux开发环境是极为欣赏的。但是，作为一个内容创作者，我也不得不使用包括Adobe Premiere Pro在内的一系列软件。所以，为了折中，我在我的电脑上安装了Hackintosh，具体来说，是macOS High Sierra。不过，它毕竟是一个非自由软件，而且说实话，黑苹果体验也确实并不完美。所以，我打算把整个黑苹果的开发环境迁移到我的128G自制移动固态硬盘上，而我的实体机，为了能够方便地进行一些开发编译，将会改为安装Arch Linux。  
首先，先介绍一下这个DIY的固态硬盘。`![](img/Hackintosh To Go/ssd1.jpg)` 我的戴尔平板是128G的版本，到手之后，我很快就买了一个256G的PM981，而更换下来的128G SC308旧开始吃灰。于是，我买了一个硬盘盒，将它改造成了一个移动SSD。`![](img/Hackintosh To Go/ssd2.jpg)`  它做移动SSD可以说是相当合适了，发热不高，速度不快不至于让USB3溢出，M.2 NGFF让它足够小巧玲珑，可以随身携带。我个人相当中意它改造成移动SSD之后的样子。`![](img/Hackintosh To Go/ssd3.jpg)`   
OK，我已经预先准备好一个Arch系统盘，`![](img/Hackintosh To Go/arch.jpg)` 接下来只需要先把macOS安装到SSD里即可。P750DM2的bios键是f2，进入BIOS确定系统设置都正常之后，从安装盘启动。  
进入启动盘，一切跟安装一般的macOS设备没有什么区别，只是注意抹掉和安装的磁盘是哪个。`![](img/Hackintosh To Go/wipe_ssd.jpg)` `![](img/Hackintosh To Go/wiping.jpg)` 我的两个2T机械硬盘，一个是NTFS协议，一个是Apple专有分区协议。显然，它们都不是Linux环境下的最优解。幸好，Apple专有协议的那块硬盘里面只有我需要用的备份文件，所以在恢复完开发环境之后我就要把那个盘抹掉。`![](img/Hackintosh To Go/wipe_complete.jpg)`   
进入安装macOS的界面`![](img/Hackintosh To Go/boot_to_install.jpg)` ，请记住要选择的是哪一个盘。我机器内置的SM961和这个固态都被命名为macOS，不过内置硬盘和外置硬盘是不同的图案，一般人不会弄错。`![](img/Hackintosh To Go/install_to.jpg)`   
选择确认，接下来就是漫长的等待。`![](img/Hackintosh To Go/installing.jpg)`   