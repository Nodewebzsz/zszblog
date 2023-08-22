##1. 介绍
```shell
wireguard是一个新的高性能VPN，它设计精巧，核心代码仅四千多行，被Linux之父Linus Torvalds称为“艺术品”。
要知道林纳斯大神平时都是喷人的，而能得到他的赞美，可见wireguard有多么优秀了。
而且wireguard相对于OpenVPN来说，配置起来更加简单，运行速度也更快。

WireGuard 是一个利用现有社会最先进的加密技术而产生的非常简单和快捷的 VPN 工具。
它的目标是比 IPsec  更快，更简单，更精简，更易用，同时避免大规模配置 IPsec 的麻烦事。
同时 WireGuard 也打算比 OpenVPN  更高效。
WireGuard 设计为通用 VPN，可在嵌入式设备和常见计算机上运行，适用于多种不同情况。
WireGuard 最初是为 Linux  内核发布的，而现在 WireGuard 已经可广泛部署并且跨平台支持。
WireGuard 目前正在大力发展，但 WireGuard  已经被认为是业内最安全，最易用和最简单的 VPN 解决方案。
```
####官网链接  [[链接](https://www.wireguard.com/)]





##我的心得



目前云服务器对新用户都会有优惠，但是不同云服务器，他们由于不在同一局域网，也就是内网不互联，通信只能开启防火墙上的端口。
自从知道wireguard后，通过wireguard可以将不同厂商的云服务器，组成局域网，实现内网互联！
而且windows上有客户端，通过简单的配置，就可以使windows本机更容易访问云服务器而不必开启各种端口，减少安全隐患！
```