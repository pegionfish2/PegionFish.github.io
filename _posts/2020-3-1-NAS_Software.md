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
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;至于内存和固态，很幸运我还能找到几台DDR3的机器，从上面又拆了一根4GB的条子下来。运气很好的是，即使使用的内存在规格上与现有的内存相差甚大，我仍然成功点亮机器。而CPU的钱则被我用来购入了一块三星的128G固态硬盘。150的高价，不用说，这显然不是极高性价比的方案。但是，基于SATA的存储方案相比于我之前基于USB3总线的存储方案在磁盘IOPS和速度上都胜过一头，也对各种操作系统有更好的支持。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后是软件。软件方面，我暂时放弃专用Linux发行版方案。不只是因为Linux下的网络调教对我来说na难度太大，或者借用京都动画撤下山本宽的名言：まだ、その域に达していない判断し。Windows下Hyper-V方案对我来说可能更为易用，且我也确实需要一个能稳定的Windows设备。目前来讲我已经成功安装windows 10、Hyper-V以及在Hyper-V里面成功部署了一套OpenWRT的虚拟机。并且，我也成功进入了控制界面。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然而令人痛苦的事情还在后面。进入OpenWRT的控制界面远远不是万事大吉。基本的配置工作仍然还无法完成，连续三天苦战后我已经决定暂时放弃这个项目，先让设备吃几天灰，之后在回去处理它。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;结果过了几天，本来可以正常工作的OpenWRT又无法正常工作了，而Windows下的网络部署比Linux还要磨人，我已经习惯Linux万物皆文件的设计哲学，再为了这点东西浪费时间学Windows不仅有法律和道德风险还浪费时间精力。Ubuntu 18.04请。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当然，Ubuntu作为通用发行版，显然不是一个开箱即用的软路由操作系统。为了将Ubuntu作为软路由Host OS使用，我们需要安装一些最基本的软件包。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dnsmasq作为DNS与DHCP服务器，Visual Studio Code作为本地文本编辑器（没错，我装了GUI。不要问我为什么，既然能用GUI为什么不用GUI？），Hollywood作为装逼工具，openssh-server和GNU Screen保证能够远程连接。接下来的配置工作主要有以下几个：  
1. 修改网络设备的名称（这个可以随意，反正有VSC自动补全到也没必要，只要自己心里有数即可）（笑）
2. 创建桥接网络
3. 配置dnsmasq
4. 配置iptables
5. 安装其他脚本与服务。这一段我会在第三篇文章中详细写。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先，修改网络设备的名称。在Ubuntu 18.04中，网络设备的名称是类似enp1s0f0这样的名称。对于一部分玩家来说这样可能并不够直观，但我这里由于网卡比较少而且一个板载一个PCIE倒还比较明了，暂时不做修改。如果需要修改名称请自行查询资料。在这篇文章中，网络设备的各命名如下：
* H81M-K上的Realtek RTL8111G是enp3s0
* Intel i340四口千兆网卡是enp1s0f0到enp1s0f3

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后就是创建桥接网络。为了保证从每个LAN进来的设备都能互相连接，就需要将LAN0-LAN3绑定为一个网段，为此就需要生成一个虚拟的桥接网口。安装bridge-utlis然后修改/etc/network/interfaces就可以完成。Ubuntu安装软件这种最简单最简单的内容在此也就不多做赘述，主要还是记得先把软件源改成中国境内的软件源获取最高速度，我用的tuna就很不错，这可能是我这辈子跟清华的唯一交集了吧w   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果你的服务器是Headless的，用你习惯的编辑器照样可以继续，不过反正你都开始钻研软路由了，基本的Linux操作和文件备份什么的就不用我再在这里逼逼赖赖了吧w  

> auto lo  
> iface lo inet loopback  
> auto enp3s0  
> allow-hotplug enp3s0  
> iface enp3s0 inet dhcp  
> auto br0  
> allow-hotplug br0  
> iface br0 inet static  
>  address 192.168.30.1  

这里就需要缩进了

> network 192.168.30.0  
> netmask 255.255.255.0  
> broadcast 192.168.30.255  
> bridge-ports enp0s0f0 enp0s0f1 enp0s0f2 enp0s0f3  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里的192.168.30.1是路由器本身的地址，也就是说我ssh bob@192.168.30.1就能ssh上这个服务器。因为24位掩码的原因，netmask这里就是255.255.255.0了（二进制下24个1就是255）。主机位全为1的地址是广播地址，这也是网络的基本常识。bridge-ports后面的这些所有接口都会加入br0这个接口的网段。至于auto和lo什么意思就请各位自己去查询，咱们不用修改它。iface eno3s0 inet dhcp就代表你上网是用DHCP的，如果是拨号上网那就需要另行修改。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;第二部就是安装并配置dnsmasq了。安装完之后检查版本号，我这边截至这篇文章发出来的版本号是2.79，但根据[官网的Changelog](http://www.thekelleys.org.uk/dnsmasq/CHANGELOG)，目前的最新版应该是2.8版，ArchLinux的软件库也包括了最新版的软件。  

> `dnsmasq -v | grep "ipset"`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用这一句语句确认你安装的dnsmasq是否有ipset功能。确认有了之后就要开始编辑配置了。我暂时没有时间慢慢阅读文件进行魔改，目前就做好最基本的工作就call it a day。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将文件改写成如下形式：

> interface = br0
> dhcp-range = 192.168.30.2,192.168.30.254,72h
> conf-dir = /etc/dnsmasq.d/

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;interface写成br0意即监听来自enp0f0s0到enp0s0f3的所有DNS与DHCP请求；dhcp-range规定了允许分配的地址范围，我这里除了作为网关使用的.1和最后的.254全部划入了可分配的地址范围，持续时间72h，也就是三天。conf-dir规定的文件夹会用于存放同样可以被dnsmasq作为配置文件读入的文件。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后，重启dnsmasq服务并把其他设备接上去应该就OK了。我这里使用我的Note FE连接网线测试。