```shell
hugo官网：https://gohugo.io/
国内：https://gohugo.org
hugo构建速度飞快，而mkdocs构建速度比较慢，目前我构建一次需要30-40秒
那为什么我不用hugo？
因为hugo的主题少，我比较喜欢mkdocs的material主题，萝卜青菜各有所爱~
```
##常见博客框架的选择
####1. hexo
```shell
hexo 以前影响力还不错，但这几年已经不如从前人们预判的那么发展的好了，
GitHub 上 hexo 项目有着 34k 个 star 看出，其中最为出名的主题便是 Next，有着 15.7k 个 star，
这也是因为 Next 目前是 hexo 主题中功能最齐全最好用的一个。
而如此之多的人使用也就意味着 hexo 这个框架的作者用收到非常多的反馈，
因此 hexo 更新优化做的很好，作者也很有动力继续做下去。
```
####但是这样的一个框架缺点也是有的：

```shell
环境配置麻烦

因为要使用 hexo 你得在本地安装 Node.js、Git，会熟练使用 GitHub，而且由于 GitHub 的特殊性，你还得学会翻墙，不然还用不了，这就对一点基础都没有的小白不是很友好了。

无后端

这意味着你没有一个后台还方便地对网站进行操作，只能通过先写好 Markdown 文件然后 Git 推送到云端。并且原生的 hexo 是没有评论系统的，想加评论还得找第三方评论系统。除此以外，一旦本地文件被你不小心删除掉了，那当你下次 push 的时候你之前的博文也就跟着丢失了。

渲染时间久

200 篇左右的博文用 Hexo 需要 10 分钟去生成静态网页，当你写博客写的时间久了之后文章多了起来，相信我，你会无法忍受这种折磨。
```
####总结：
```shell

hexo 适合有一定基础的人，然后写博客时间不长或者只是随便写来玩的人。
当然尤其其广泛的传播性，当你遇到问题的时候拿到网上去搜一般都是有解决方案的，
这也可以为你省下一点力气。

最后，如果你想用 hexo，我建议主题用 Next。
```
##2. Hugo
```shell
Hugo 几年前的影响力是不如 hexo 的，但现在越来越多的人从 hexo 迁移到了 Hugo，
Hugo使用人数也多了起来，GitHub 上 Hugo 项目有 56.2k 个 star，已远远超过了 hexo，
因此你也不用太担心 Hugo 会不会太小众化的问题，但是 Hugo 上的主题选择会更少一些，
其中最受欢迎的是 wowchemy，但也仅有 6.1k 个star，而本站采用的是 LoveIt 主题， 它的 star 就更少了，才 1.6k 个。
当然，如果你是搞前端开发的，或者乐意自己写主题，那这些就不重要了。
```
####Hugo优点：

```shell
速度快

Hugo 采用 Go 语言编写，它的速度用作者的话来形容就是世界上最快的构建网站工具。并且 Hugo 是即时渲染的，这意味着你可以边写边改样式，直到你满意为止。即使是你写了几百篇文章，它也能在几秒之内全部渲染完成。

    The world’s fastest framework for building websites

配置更为简单

你需要安装只是 Hugo，不像 hexo 还得安装 Node.js。并且Hugo 中是不区分站点和主题的配置文件的，Hugo 中只有一个位于站点根目录下的 config.toml 配置文件，你只用在这里面进行修改就可以了。

方便自定义

你可以在不修改主题文件的前提下方便地定制主题。在 Hugo 中，如果你想要定制主题，你只需在站点目录下新建相应的文件即可。这是非常利于主题的维护的，你只需使用 Git 的 submodule 的方式安装 Hugo 的主题，然后更新时只需直接在站点根目录下敲一条命令回车即可，非常方便！
```
####缺点：

```shell
主题比较少，很可能大家都是用的同一个主题，并且主题作者更新会更少一点。
```
####总结：

```shell
如果你喜欢 DIY，我建议使用 Hugo。如果你是个专业博主，写了很多文章需要渲染，我建议使用 Hugo！
```
##3. Typecho
```shell
这是一个非常轻量级的博客框架，但是需要你拥有一个服务器。并且它对服务器要求极低，
即使只有 512M 内存或是更低，它也能跑起来。它可以满足你对博客的基本需求，
而且 Typecho 是带后端的，意味着只要你能上网，你就可以自由地写你的文章，不会被设备所拘束。
当然，你将免除配置环境的苦恼。
```
####缺点：
```shell

更新慢

奇慢无比，作者已经 9 年没有进行更新了，一些插件也已经不能用了。

自由度低

你不能随心所欲地进行 DIY，当然，如果你只是用来写博客的话问题不是很大。
```
##4. WordPress
```shell
世界上最受欢迎的建站工具！具体有多受欢迎？每三个网站就有一个是 WordPress 搭建，
并且美国白宫自2017年起，其官网 Whitehouse.gov 网站的
內容管理系統（Content management system，CMS）从 Drupal 换成 WordPress！

WordPress 是一个以 PHP 和 MySQL 为平台的自由开源的博客软件和内容管理系统。WordPress 具有插件架构和模板系统。截至2018年4月，排名前1000万的网站中超过30.6%使用WordPress 。WordPress是最受欢迎的网站内容管理系统。全球有大约30%的网站(7亿5000个)都是使用WordPress架设网站的。WordPress 是目前因特网上最流行的博客系统。
并且 WordPress 并不只是可以用来写博客，它能用来打造一切你想要的网站， 哪怕是用来建个电商网站也没有问题！
```
####优点：
```shell

超广泛传播性

你在使用 WordPress 遇到的任何问题，你都可以在网上找到对应的解决方案，它的使用人数之多以至于每一个坑都有人替你趟过了！

DIY 自由度高，难度低

你可以随心所欲地添加插件，WordPress 提供了大量的优质插件，甚至有大量的人就以制作 WordPress 上的插件谋生！

安装简单

网上有非常多的 WordPress 一键安装脚本，你可以根据自己的需求进行选择，无需面对安装过程中的问题！并且其安装时间非常短，只需要5分钟就能搞定！
```
####缺点：
```shell

需要有一定性能的服务器

PHP，MySQL这些对服务器有一定的要求，会占用比较多的内存，它不像 Typecho 一样轻便。

太过臃肿，不简洁

太多的功能与选择造成了页面的繁琐，并且你会对着页面一直修改，这不利于你专心地撰写博文。
```
####总结：适合有服务器，懒得折腾环境配置，喜欢开箱即用的人。

———————————————— 版权声明：本文为CSDN博主「su14772」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。 原文链接：https://blog.csdn.net/sk14772/article/details/122374376