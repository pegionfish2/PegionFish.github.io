---
layout: post
author: Bob Guo
title: 图床记（1）
subtitle: 将博文中的图片转移到七牛云
date: 2019-4-16
tags:  博客 图床 云 七牛
published: true
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上次说过不当鸽子之后，还是鸽了很久。这点我表示抱歉。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;自己的主力机器终于回到自己手中，本来想安装黑苹果或者Linux的，但是考虑到两者都有一定的不便，我还是打算在后面买了新固态之后再考虑装双系统的事宜。至于现在，还是先忍受Windows的一些不便吧（比如GNU工具链的缺失）。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我自己有了一个新的项目，用Python开发一套跑团引擎，大致上可以说是一个改版的、多选择支的VN引擎配合一个随机数生成器（用于计算骰子女神的微笑的）。不过，这个项目暂时无法开展。我Python的功底实在太差，由于学习C语言的关系我基本已经彻底放弃Python，所以现在得重新捡起来研究。不过，一旦情况允许我将会马上开始着手编写就是了。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;那么今天，我打算先把博客的事情解决一下。在之前的一篇博文里，我放了一些图片在repo的img文件夹里，但是它们都无法被加载。所以，我注册了一个七牛云，打算用七牛云作为图床。反正我这个博客没人看，免费的流量足够让我使用了。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;看看这个界面，![Alt text](/img/imgbed/qiniu/proove.png)虽然我已经把图片放到img文件夹里，也做了正确的映射，还是发生这种情况。那么，这种情况就应该换家。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先，下载一个七牛的工具。我使用的浏览器是Chrome，所以登录这个地址：

   >    https://chrome.google.com/webstore/detail/%E4%B8%83%E7%89%9B%E4%BA%91%E5%9B%BE%E5%BA%8A/fmpbbmjlniogoldpglopponaibclkjdg?hl=zh-CN

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;下载一个开源的七牛云工具。![Alt text](/img/imgbed/qiniu/download.png)当然，其他的工具也OK，我这里比较懒得找就只用这个就好了。打开它，第一次使用会需要输入AK、SK和Bucket。![Alt text](/img/imgbed/qiniu/first_time.png)它提供了一个链接可以跳转到七牛开发者面板，就可以找到你的AK、SK数据。![Alt text](/img/imgbed/qiniu/key.png)bucket名称是自己设定的，而域名，在我的情况下就需要重新“挂载”了。选择融合CDN-域名管理，就可以进行域名的编辑。但是很奇怪，我通过阿里云注册的域名（bobguo.top）显示无备案，全国公安机关互联网安全管理服务平台也查不到这个域名的数据。那么，这次就先这样吧，这个问题可能需要更多处理，明天我会继续更新的。![Alt text](/img/imgbed/qiniu/.png)