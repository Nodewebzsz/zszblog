##1. 介绍
```shell
1.grep全拼：
global search regular expression and print out the line

2.grep作用：
文本搜索工具，根据用户指定的“模式”（过滤条件）对目标文件逐行进行匹配检查，打印匹配到的行

3.模式：由正则表达式的元字符及文本字符所编写的过滤条件

4.语法：
grep [options] [pattern] file
命令   参数      匹配模式  文本数据

#4.1 参数
    -q：--quiet，--silent，静默模式，即不输出任何信息！
    -v：排除匹配结果
    -n：显示匹配行与行号
    -i：不区分大小写
    -c：只统计匹配的行数
    -E：支持扩展正则
    --colorauto：为grep过滤结果添加颜色
    -w：只匹配过滤的单词
    -o：只输出匹配的内容

#4.2 匹配模式，就是你想要找的东西，可以是普通的文字符号，也可以是正则表达式    

5.grep命令是Linux系统中最重要的命令之一，功能是从文本文件或管道数据流中筛选匹配的行和数据
  如果再配合正则表达式，功能十分强大，是Linux运维人员必备的命令！
```
##2. 常见使用场景

```shell

1.过滤端口或者服务
netstat -tunlp|grep mysql
ps -ef|grep nginx

2.查看没有注释的配置文件
grep -Ev '^$|^#' /etc/nginx/nginx.conf

3.查找日志文件中错误信息等
grep 'err' err.log

```