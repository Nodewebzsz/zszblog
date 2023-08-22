##一句话：
```shell
Flask is a micro web development framework for Python.
（Flask是一个基于Python的Web开发微框架。）
```
##一、什么是Web框架？
```shell
简单来说，Web框架是用来帮助你更简单高效的编写Web应用的软件框架。
当你在浏览器里访问一个网址，发起HTTP请求，这时Web框架就负责处理这个请求，
分配不同的访问地址到相应的代码，然后生成HTML，创建带有内容的HTTP响应。
借助Web框架，你不用编写处理HTTP请求与响应等等这些底层代码。更详细的介绍见这篇文章。

Python的著名Web框架有Django、Pyramid、Tornado、webpy、Zope等。
```
##二、为什么说Flask是微框架？
```shell
之所以说Flask是微框架，因为它仅仅实现了Web应用的核心功能：
Flask由两个主要依赖组成（提供路由、调试和Web服务器网关接口的Werkzeug和提供模板的Jinja2）。

其他的一切（比如数据库集成，表单处理，文件上传，用户认证）都由第三方库来完成，
如果插件满足不了你的需求，你也可以自行开发。
```
##三、Flask还有什么特点？
```shell
良好的文档
丰富的插件
包含开发服务器和调试器（debugger）
集成支持单元测试
RESTful请求调度
支持安全cookies
基于Unicode
```
##四、哪些网站使用Flask

```shell
基于Flask实现的最大的网站应该算是Pinterest了， 不过你不应该过于关心这些，无论是一个简单的便签本程序，还是一个大型社交网站，Flask都可以实现， 只要你有相应的能力来驾驭它。：）
```