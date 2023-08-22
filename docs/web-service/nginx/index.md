
##1. 介绍
```shell
nginx是一款优秀的高性能web服务器，反向代理服务器，负载均衡服务器，邮件代理服务器。
```
##2. 如何查看网站使用的web服务器？
```shell
# 查看网站使用的web服务器命令
curl - I 域名 
# 举例
curl -I taobao.com

# tengine是阿里巴巴基于nginx二次开发的适合淘宝高并发的产品
root@baiduyun:~# curl -I taobao.com
HTTP/1.1 302 Found
Server: Tengine
Date: Tue, 15 Feb 2022 22:34:02 GMT
Content-Type: text/html
Content-Length: 258
Connection: keep-alive
Location: http://www.taobao.com/

# apache
root@baiduyun:~# curl -I baidu.com
HTTP/1.1 200 OK
Date: Tue, 15 Feb 2022 22:34:09 GMT
Server: Apache
Last-Modified: Tue, 12 Jan 2010 13:48:00 GMT
ETag: "51-47cf7e6ee8400"
Accept-Ranges: bytes
Content-Length: 81
Cache-Control: max-age=86400
Expires: Wed, 16 Feb 2022 22:34:09 GMT
Connection: Keep-Alive
Content-Type: text/html

root@baiduyun:~# curl -I chupeng.site
HTTP/1.1 200 OK
Date: Tue, 15 Feb 2022 22:34:19 GMT
Server: Apache/2.4.41 (Ubuntu)
Last-Modified: Fri, 21 Jan 2022 06:51:32 GMT
ETag: "9906-5d6120c9c1db7"
Accept-Ranges: bytes
Content-Length: 39174
Vary: Accept-Encoding
Content-Type: text/html
```
##3. nginx优势
```shell
1.配置文件简单易懂
2.支持url地址重写
3.运行稳定，宕机几率小
4.支持静态文件压缩，节省带宽
5.支持热部署
```