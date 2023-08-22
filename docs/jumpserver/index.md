##等保¶
```shell
# https://www.cnblogs.com/llddhh/p/14553764.html
```
![jumpserver1](../../../assets/images/jumpserver1.png)

![jumpserver2](../../../assets/images/jumpserver2.png)

##官网¶
```shell
JumpServer官网：https://www.jumpserver.org/
# github：https://github.com/jumpserver/
JumpServer官方文档： https://docs.jumpserver.org/zh/master/
JumpServer在B站发布的课程： https://www.bilibili.com/video/BV19D4y1S7s4/
```
##1. 跳板机/堡垒机是什么？¶
```shell
在说JumpServer之前，需要先了解一下跳板机/堡垒机的概念。

1.百度说明：
跳板机，也称堡垒机，是一类可作为跳板批量操作远程设备的网络设备，
是系统管理员或运维人员常用的操作平台之一。

2.结合日常理解：
跳板，在生活中的使用就是可以通过它来跳更高或者更远的地方，
它在其中起到了一个助力的作用，通过它可以使我们达到之前无法到达的地方。

3.结合环境试例说明：

现在需要登录到公司内网服务器，正常的登录流程为：

    1.通过笔记本SSH到公网服务器上
    2.由公网服务器SSH到内网服务器

在这个过程中，这个公网服务器就相当于是一个跳板机，通过它来完成登录内网服务器操作，这就是对跳板机的简单理解。

但此方式显然没有安全性可言，功能方面更是只有登录操作，最终由需求使得堡垒机这类软件的产生。
```
##2. JumpServer是什么？¶
```shell
JumpServer是FIT2CLOUD（飞致云）旗下的软件产品，是全球首款完全开源的堡垒机软件，
采用Python / Django 开发，分社区免费版和企业付费版两种。
因其开源，无插件，Web界面美观，操作方便，分布式，符合4A规范等特点，
被很多企业用于内部资产（物理机，云主机等）的管理。

其中最重要的就是符合4A规范，可以完成身份验证，使我们轻松地管理各种人员的资产和权限，
并且有安全审计功能，记录用户各种操作。
```
####1. 详细介绍¶
```shell
JumpServer 是全球首款完全开源的堡垒机, 使用 GNU GPL v2.0 开源协议, 是符合 4A 的专业运维审计系统。

JumpServer 使用 Python / Django 进行开发, 遵循 Web 2.0 规范, 
配备了业界领先的 Web Terminal 解决方案, 交互界面美观、用户体验好。

JumpServer 采纳分布式架构, 支持多机房跨区域部署, 中心节点提供 API, 各机房部署登录节点, 
可横向扩展、无并发访问限制。

JumpServer 现已支持管理 SSH、 Telnet、 RDP、 VNC 协议资产。
```
####2. 特点说明¶
```shell
开源: 零门槛，线上快速获取和安装；
分布式: 轻松支持大规模并发访问；
无插件: 仅需浏览器，极致的 Web Terminal 使用体验；
多云支持: 一套系统，同时管理不同云上面的资产；
云端存储: 审计录像云端存储，永不丢失；
多租户: 一套系统，多个子公司和部门同时使用。
```
####3. 功能列表¶
![jumpserver3](../../../assets/images/jumpserver3.png)

![jumpserver4](../../../assets/images/jumpserver4.png)

![jumpserver5](../../../assets/images/jumpserver5.png)

![jumpserver6](../../../assets/images/jumpserver6.png)

##3. 结尾¶
```shell
总的来说，JumpServer是一款符合企业实际应用的开源堡垒机软件，功能强大且广受欢迎。
官网上就列举了很多使用了JumpServer的知名互联网公司，小红书，趣头条，得物，顺丰，
甚至还看到了我常玩的米哈游，这又进一步说明了JumpServer在堡垒机方面的优秀。
```
———————————————— 版权声明：本文为CSDN博主「风雨兼程，披星戴月。」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。 原文链接：https://blog.csdn.net/qq_42534026/article/details/110695509

