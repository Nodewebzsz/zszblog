##介绍
```shell
# 官网：https://keepalived.org/
keepalived软件，起初是专为LVS负载均衡设计的，用来管理并监控LVS集群系统各个服务节点的状态。
后来又加入了可以实现高可用的VRRP功能，因此它除了能够管理lvs外，还可以作为其他服务的高可用解决方案，
如nginx、haproxy、mysql等。

keepalived软件主要通过VRRP协议实现高可用功能。
VRRP：Virtual Router Redundancy Protocol（虚拟路由器冗余协议）。
VRRP出现的目的就是为了解决静态路由单点故障的问题，它能够保证当个别节点宕机时，整个网络可以不间断的运行。

```
