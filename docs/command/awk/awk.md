##1. 案例1
####1. 准备案例文件
```shell
cd /tmp
vim cp.txt
cp1 cp2 cp3 cp4 cp5
cp6 cp7 cp8 cp9 cp10
```
####2. 取出第二列
```shell
cat cp.txt |awk '{print $2}' 

# awk默认以空格为分隔符，且多个空格也识别为一个空格
```
```shell
root@baiduyun:/tmp# cat cp.txt |awk '{print $2}'
cp2
cp7
```
####3. 一次性输出多列
```shell
#1.多列之间有“，”则输出结果中多列之间以空格间隔
awk '{print $1,$2}' cp.txt

#2.多列之间没有“，”，则输出结果也直接相连！
awk '{print $1$4$5}' cp.txt
awk '{print $1 $5 $4}' cp.txt # 与上面结果一致！
```
```shell
 #1.多列之间有“，”则输出结果中多列之间以空格间隔
root@baiduyun:/tmp# awk '{print $1,$2}' cp.txt
cp1 cp2
cp6 cp7

 #2.多列之间没有“，”，则输出结果也直接相连！
root@baiduyun:/tmp# awk '{print $1$4$5}' cp.txt
cp1cp4cp5
cp6cp9cp10
root@baiduyun:/tmp# awk '{print $1 $5 $4}' cp.txt 
cp1cp5cp4
cp6cp10cp9
```
####4. 自定义输出内容
```shell

awk '{print "第一列：",$1,"第二列：",$2,"第三列：",$3}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print "第一列：",$1,"第二列：",$2,"第三列：",$3}' cp.txt
第一列： cp1 第二列： cp2 第三列： cp3
第一列： cp6 第二列： cp7 第三列： cp8
```
####5. 输出整行信息
```shell
awk '{print}' cp.txt
awk '{print $0}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print}' cp.txt
cp1 cp2 cp3 cp4 cp5
cp6 cp7 cp8 cp9 cp10
root@baiduyun:/tmp# awk '{print $0}' cp.txt
cp1 cp2 cp3 cp4 cp5
cp6 cp7 cp8 cp9 cp10
```
####6. 每一行开头添加内容！
```shell
awk '{print "每一行的内容是："$0}' cp.txt

# 这样的话，是不是可以将文件全部注释？
awk '{print "#"$0}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print "每一行的内容是："$0}' cp.txt
每一行的内容是：cp1 cp2 cp3 cp4 cp5
每一行的内容是：cp6 cp7 cp8 cp9 cp10
root@baiduyun:/tmp#

# 将文件全部注释
root@baiduyun:/tmp# awk '{print "#"$0}' cp.txt
#cp1 cp2 cp3 cp4 cp5
#cp6 cp7 cp8 cp9 cp10
```
##2. 案例2
####1. 准备案例文件
```shell
# 以/etc/passwd文件为例
cd /tmp
cat /etc/passwd >pwd.txt
```
####2. 显示文件的第5行
```shell
awk 'NR==5' pwd.txt
```
```shell
root@baiduyun:/tmp# awk 'NR==5' pwd.txt
sync:x:4:65534:sync:/bin:/bin/sync
```

####3. 显示文件2-5行
```shell
awk 'NR==2,NR==5' pwd.txt
```
```shell
root@baiduyun:/tmp# awk 'NR==2,NR==5' pwd.txt
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```
####4. 显示文件的最后一列
```shell
# NF：一共有多少列
awk '{print $NF}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print $NF}' cp.txt
cp5
cp10
```
####5. 显示第2-4行的第5列
```shell
awk 'NR==2,NR==4{print $5}' cp.txt
```
```shell
root@baiduyun:/tmp# awk 'NR==2,NR==4{print $5}' cp.txt
cp10
root@baiduyun:/tmp# awk -F ":" 'NR==2,NR==4{print}' pwd.txt
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
root@baiduyun:/tmp# awk -F ":" 'NR==2,NR==4{print $5}' pwd.txt
daemon
bin
sys
```shell
####6. 给每一行添加行号
```shell
awk '{print NR,$0}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print NR,$0}' cp.txt
1 cp1 cp2 cp3 cp4 cp5
2 cp6 cp7 cp8 cp9 cp10
```
####7. 显示第一列，倒数第二列，最后一列
```shell
awk '{print $1,$(NF-1),$NF}' cp.txt
```
```shell
root@baiduyun:/tmp# awk '{print $1,$(NF-1),$NF}' cp.txt
cp1 cp4 cp5
cp6 cp9 cp10
```
##3. 分隔符案例
```shell
# 输入分隔符：默认空格，英文是field seperator，FS
# 输出分隔符：output field seperator，OFS
```
####1. 指定输入分隔符
#####1.指定":"为分隔符
```shell
awk -F ':' '{print $1}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -F ':' '{print $1}' pwd.txt
root
daemon
bin
sys
sync
games
...
```shell
#####2.通过修改内置变量来指定：为分隔符
```shell
awk -v FS=":" '{print $1}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -v FS=":" '{print $1}' pwd.txt
root
daemon
bin
sys
sync
games
```
####2. 指定输出分隔符
#####1.指定---
```shell
awk -F ":" -v OFS="---" '{print $1,$NF}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -F ":" -v OFS="---" '{print $1,$NF}' pwd.txt
root---/bin/bash
daemon---/usr/sbin/nologin
bin---/usr/sbin/nologin
sys---/usr/sbin/nologin
sync---/bin/sync
games---/usr/sbin/nologin
```shell
#####2.指定制表符
```shell
awk -F ":" -v OFS="\t" '{print $1,$NF}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -F ":" -v OFS="\t" '{print $1,$NF}' pwd.txt
root    /bin/bash
daemon  /usr/sbin/nologin
bin     /usr/sbin/nologin
sys     /usr/sbin/nologin
sync    /bin/sync
games   /usr/sbin/nologin
```
##4. awk变量案例
####1. 输入分隔符
```shell
#1. 输出第一列
awk -v FS=":" '{print $1}' pwd.txt

#2. 输出第一列，并且每一行有行号和列数
awk -v FS=":" '{print NR,NF,$1}' pwd.txt

awk -v FS=":" '{print NR,$1,$(NF-1)}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -v FS=":" '{print $1}' pwd.txt
root
daemon
bin
sys
sync
games


root@baiduyun:/tmp# #2. 输出第一列，并且每一行有行号和列数
root@baiduyun:/tmp# awk -v FS=":" '{print NR,NF,$1}' pwd.txt
1 7 root
2 7 daemon
3 7 bin
4 7 sys
5 7 sync
6 7 games


root@baiduyun:/tmp# awk -v FS=":" '{print NR,$1,$(NF-1)}' pwd.txt
1 root /root
2 daemon /usr/sbin
3 bin /bin
4 sys /dev
5 sync /bin
6 games /usr/games
7 man /var/cache/man
```
####2. 输出换行符
```shell
# 内置变量ORS:输出换行符。默认回车

#1. 指定输出换行符
awk -F ":"  '{print NR,$0}' pwd.txt
awk -F ":" -v ORS="@@@" '{print NR,$0}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk -F ":"  '{print NR,$0}' pwd.txt
1 root:x:0:0:root:/root:/bin/bash
2 daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
3 bin:x:2:2:bin:/bin:/usr/sbin/nologin
4 sys:x:3:3:sys:/dev:/usr/sbin/nologin
5 sync:x:4:65534:sync:/bin:/bin/sync
6 games:x:5:60:games:/usr/games:/usr/sbin/nologin


root@baiduyun:/tmp# awk -F ":" -v ORS="@@@" '{print NR,$0}' pwd.txt
1 root:x:0:0:root:/root:/bin/bash@@@2 daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin@@@3 bin:x:2:2:bin:/bin:/usr/sbin/nologin@@@4 sys:x:3:3:sys:/dev:/usr/sbin/nologin@@@5 sync:x:4:65534:sync:/bin:/bin/sync@@@6 games:x:5:60:games:/usr/games:/usr/sbin/nologin@@@7 man:x:6:12:man:/var/cache/man:/usr/sbin/nologin@@@
```shell

####3. FILENAME
```shell
# 内置变量：FILENAME：显示awk正在处理的文件的名字
awk '{print FILENAME,FNR,$0}' pwd.txt
```
```shell
root@baiduyun:/tmp# awk '{print FILENAME,FNR,$0}' pwd.txt
pwd.txt 1 root:x:0:0:root:/root:/bin/bash
pwd.txt 2 daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
pwd.txt 3 bin:x:2:2:bin:/bin:/usr/sbin/nologin
pwd.txt 4 sys:x:3:3:sys:/dev:/usr/sbin/nologin
pwd.txt 5 sync:x:4:65534:sync:/bin:/bin/sync
pwd.txt 6 games:x:5:60:games:/usr/games:/usr/sbin/nologin
pwd.txt 7 man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
```
####4. ARGV
```shell
# ARGV 表示数组，保存的时命令行所给的参数

awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[0],$0}' cp.txt
# ARGV[0] :awk

awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[1],$0}' cp.txt
# ARGV[1] :cp.txt

awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[0],ARGV[1],ARGV[2]}' cp.txt pwd.txt
# ARGV[0] :awk
# ARGV[1] :cp.txt
# ARGV[2] :pwd.txt
```
```shell
root@baiduyun:/tmp# awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[0],$0}' cp.txt
开始使用awk操作了
awk cp1 cp2 cp3 cp4 cp5
awk cp6 cp7 cp8 cp9 cp10


root@baiduyun:/tmp# awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[1],$0}' cp.txt
开始使用awk操作了
cp.txt cp1 cp2 cp3 cp4 cp5
cp.txt cp6 cp7 cp8 cp9 cp10


root@baiduyun:/tmp# awk 'BEGIN{print "开始使用awk操作了"}{print ARGV[0],ARGV[1],ARGV[2]}' cp.txt pwd.txt
开始使用awk操作了
awk cp.txt pwd.txt
awk cp.txt pwd.txt
awk cp.txt pwd.txt
awk cp.txt pwd.txt
awk cp.txt pwd.txt
awk cp.txt pwd.txt
```
####5. 自定义变量
```shell
#1.方法1
awk -v VarName="awk牛逼" 'BEGIN{print VarName}{print $0}' cp.txt

#2.方法2
awk 'BEGIN{VarName="awk牛逼";VarName1="awk牛逼1";print VarName,VarName1}'

#3.方法3：间接引用shell变量
VarName="awk牛逼"
awk -v VarName=$VarName 'BEGIN{print VarName}'

#4. 案例
awk -v myname="chupeng" 'BEGIN{print "My name is",myname}'
```
```shell
root@baiduyun:/tmp# awk -v VarName="awk牛逼" 'BEGIN{print VarName}{print $0}' cp.txt
awk牛逼
cp1 cp2 cp3 cp4 cp5
cp6 cp7 cp8 cp9 cp10


root@baiduyun:/tmp# awk 'BEGIN{VarName="awk牛逼";VarName1="awk牛逼1";print VarName,VarName1}'
awk牛逼 awk牛逼1


root@baiduyun:/tmp# VarName="awk牛逼"
root@baiduyun:/tmp# awk -v VarName=$VarName 'BEGIN{print VarName}'
awk牛逼


root@baiduyun:/tmp# awk -v myname="chupeng" 'BEGIN{print "My name is",myname}'
My name is chupeng
```
##5. printf格式化案例
####1. 准备案例文件
```shell
cd /tmp
vim cp.txt
他一定很爱你
也把我比下去
```
####2. printf输出测试（没有换行符）
```shell

root@baiduyun:/tmp# awk '{printf $0}' cp.txt
他一定很爱你也把我比下去root@baiduyun:/tmp#
```
####3. 演示print和printf的区别
```shell
#1. 准备案例文件
vim nb.txt
nb1
nb2
nb3

#2.print
awk '{print $1}' nb.txt

#3.printf
awk '{printf $1}' nb.txt
```
```shell
root@baiduyun:/tmp# awk '{print $1}' nb.txt
nb1
nb2
nb3
root@baiduyun:/tmp# awk '{printf $1}' nb.txt
nb1nb2nb3
```
####4. 给printf添加格式
```shell
#1.
awk '{printf "%s\n",$1}' nb.txt
# 这样处理后，与print输出一致！

#2.
awk '{printf "%s--\n",$1}' nb.txt
```
```shell
root@baiduyun:/tmp# awk '{printf "%s\n",$1}' nb.txt
nb1
nb2
nb3
# 这样处理后，与print输出一致！

root@baiduyun:/tmp# awk '{printf "%s--\n",$1}' nb.txt
nb1--
nb2--
nb3--
# 自定义格式
```
####5. printf演示1
```shell
#1.
printf "%s--\n" a b c d e

#2.
awk 'BEGIN{printf "%d\n",1,2,3,4}'

#3.
awk 'BEGIN{printf "%d\n%d\n",1,2,3,4}'

#4.
awk 'BEGIN{printf "%d\n %d\n %d--\n",1,2,3,4}'
```
```shell
root@baiduyun:/tmp# printf "%s--\n" a b c d e
a--
b--
c--
d--
e--
root@baiduyun:/tmp#
root@baiduyun:/tmp# awk 'BEGIN{printf "%d\n",1,2,3,4}'
1
root@baiduyun:/tmp# awk 'BEGIN{printf "%d\n%d\n",1,2,3,4}'
1
2
root@baiduyun:/tmp# awk 'BEGIN{printf "%d\n %d\n %d--\n",1,2,3,4}'
1
 2
 3--
```
##6. printf演示2
####1. 演示文件
```shell
vim nb.txt
nb1 nb2 nb3
nb4 nb5 nb6
nb7 nb8 nb9
nb10
```
####2. printf格式化输出文件内容
```shell
#1.
awk '{printf "第一列：%s    第二列：%s  第三列：%s\n",$1,$2,$3}' nb.txt

root@baiduyun:/tmp# awk '{printf "第一列：%s第二列：%s第三列：%s\n",$1,$2,$3}' nb.txt
第一列：nb1第二列：nb2第三列：nb3
第一列：nb4第二列：nb5第三列：nb6
第一列：nb7第二列：nb8第三列：nb9
第一列：nb10第二列：第三列：
```
##7. 格式化输出passwd文件
```shell
#1.文件
cat /etc/passwd > /tmp/pwd.txt
cd /tmp

#2.格式化
awk -F ":" 'BEGIN{printf "%-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\n","用户名","密码","UID","GID","用户注释","用户家目录","用户使用的解释器"} {printf "%-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\n",$1,$2,$3,$4,$5,$6,$7}' pwd.txt

# 参数解释
    %s：格式替换符，替换字符串
    %s\t：格式化字符串后，添加制表符
    %-25s：依然是格式化字符串，-代表左对齐，25个字符长度！
```
```shell
root@baiduyun:/tmp# awk -F ":" 'BEGIN{printf "%-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\n","用户名","密码","UID","GID","用户注释","用户家目录","用户使用的解释器"} {printf "%-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\t %-25s\n",$1,$2,$3,$4,$5,$6,$7}' pwd.txt
用户名                           密码                            UID                             GID                             用户注释                        用户家目录                         用户使用的解释器
root                             x                               0                               0                               root                            /root                      /bin/bash
daemon                           x                               1                               1                               daemon                          /usr/sbin                  /usr/sbin/nologin
bin                              x                               2                               2                               bin                             /bin                       /usr/sbin/nologin
...
```
##8. awk模式
####1. BEGIN，END模式案例
```shell
#1
awk 'BEGIN{print "一起来学习awk的BEGIN模式啊"}'

#2.
awk 'BEGIN{print "一起来学习awk的BEGIN模式啊"}{print $1}' nb.txt
# 先执行BEGIN的，再执行后面的！

#3.
awk '{print $1,$3} END{print "一起来学习awk的END模式啊"}' nb.txt
# 先执行前面的，再执行END的！

#4.
awk 'BEGIN{print "处理文本之前，awk会先执行BEGIN中的动作！"}{print $0}END{print "最后执行END中的动作！"}' nb.txt
```
```shell
root@baiduyun:/tmp# #1
root@baiduyun:/tmp# awk 'BEGIN{print "一起来学习awk的BEGIN模式啊"}'
一起来学习awk的BEGIN模式啊
root@baiduyun:/tmp#
root@baiduyun:/tmp# #2.
root@baiduyun:/tmp# awk 'BEGIN{print "一起来学习awk的BEGIN模式啊"}{print $1}' nb.txt
一起来学习awk的BEGIN模式啊
nb1
nb4
nb7
nb10
root@baiduyun:/tmp#
root@baiduyun:/tmp# #3.
root@baiduyun:/tmp# awk '{print $1,$3} END{print "一起来学习awk的END模式啊"}' nb.txt
nb1 nb3
nb4 nb6
nb7 nb9
nb10
一起来学习awk的END模式啊
root@baiduyun:/tmp#
root@baiduyun:/tmp# #4.
root@baiduyun:/tmp# awk 'BEGIN{print "处理文本之前，awk会先执行BEGIN中的动作！"}{print $0}END{print "最后执行END中的动作！"}' nb.txt
处理文本之前，awk会先执行BEGIN中的动作！
nb1 nb2 nb3
nb4 nb5 nb6
nb7 nb8 nb9
nb10
最后执行END中的动作！
```
####2. 关系运算符模式案例
```shell
#1.第二行
awk 'NR==2{print $0}' nb.txt

#2.前3行
awk 'NR<4{print $0}' nb.txt

#3.除了第三行
awk 'NR!=3{print $0}' nb.txt
```
```shell
root@baiduyun:/tmp# #1.
root@baiduyun:/tmp# awk 'NR==2{print $0}' nb.txt
nb4 nb5 nb6
root@baiduyun:/tmp#
root@baiduyun:/tmp# #2.
root@baiduyun:/tmp# awk 'NR<4{print $0}' nb.txt
nb1 nb2 nb3
nb4 nb5 nb6
nb7 nb8 nb9
root@baiduyun:/tmp#
root@baiduyun:/tmp# #3.
root@baiduyun:/tmp# awk 'NR!=3{print $0}' nb.txt
nb1 nb2 nb3
nb4 nb5 nb6
nb10
```
####3. awk与正则表达式
```shell
# 正则表达式主要与awk的 pattern模式 结合使用
    # 不指定模式，awk每一行都会执行对应的动作
    # 指定了模式，只有被模式匹配到的、符合条件的行才会执行动作

# awk使用正则的语法
    grep '正则表达式' pwd.txt
    awk '/正则表达式/动作' pwd.txt
```shell    
#####1. 找出pwd.txt中以ro开头的行
```shell
#1.grep过滤
grep '^ro' pwd.txt

#2.awk过滤
awk '/^ro/{print $0}' pwd.txt
```
```shell
root@baiduyun:/tmp# #1.grep过滤
root@baiduyun:/tmp# grep '^ro' pwd.txt
root:x:0:0:root:/root:/bin/bash
root@baiduyun:/tmp#
root@baiduyun:/tmp# #2.awk过滤
root@baiduyun:/tmp# awk '/^ro/{print $0}' pwd.txt
root:x:0:0:root:/root:/bin/bash
```
#####2. 找出pwd.txt中禁止登录的用户¶
```shell
# 就是找到/sbin/nologin的行
# 注意：正则表达式中如果出现了“/”，则需要进行转义！

#1. grep
grep -n '/sbin/nologin$' pwd.txt

#2. awk
awk '/\/sbin\/nologin$/{print NR,$0}' pwd.txt
```
```shell
root@baiduyun:/tmp# #1. grep
root@baiduyun:/tmp# grep -n '/sbin/nologin$' pwd.txt
2:daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
3:bin:x:2:2:bin:/bin:/usr/sbin/nologin
4:sys:x:3:3:sys:/dev:/usr/sbin/nologin
6:games:x:5:60:games:/usr/games:/usr/sbin/nologin
...
root@baiduyun:/tmp# #2. awk
root@baiduyun:/tmp# awk '/\/sbin\/nologin$/{print NR,$0}' pwd.txt
2 daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
3 bin:x:2:2:bin:/bin:/usr/sbin/nologin
4 sys:x:3:3:sys:/dev:/usr/sbin/nologin
6 games:x:5:60:games:/usr/games:/usr/sbin/nologin
...
```

#####3. 找出文件的区间内容
```shell
# 正则模式
    awk '/正则/{动作}' file
# 行范围模式
    awk '/正则1/,/正则2/{动作}' file

#1. 找出mail用户到nobody用户之间的内容
awk '/^mail/,/^nobody/{print $0}' pwd.txt

#2. 关系表达式模式
awk 'NR>=4 && NR<=8 {print $0}' pwd.txt
```
```shell
root@baiduyun:/tmp# #1. 找出mail用户到nobody用户之间的内容
root@baiduyun:/tmp# awk '/^mail/,/^nobody/{print $0}' pwd.txt
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
root@baiduyun:/tmp#
root@baiduyun:/tmp# #2. 关系表达式模式
root@baiduyun:/tmp# awk 'NR>=4 && NR<=8 {print $0}' pwd.txt
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
```
####4. awk企业实战nginx日志
```shell
#1. 统计日志的访客IP数量
awk '{print $1}' access.log |sort -n |uniq|wc -l

#2. 查看访问最频繁的前10个IP
awk '{print $1}' access.log |sort -n |uniq -c |sort -nr|head -10
```
```shell
ubuntu@zabbix:/var/log/nginx$ awk '{print $1}' access.log.1 |sort -n |uniq -c|wc -l
8
ubuntu@zabbix:/var/log/nginx$ awk '{print $1}' access.log.1 |sort -n |uniq -c|sort -rn |head -10
     10 91.194.84.88
      2 42.157.194.16
      2 39.99.137.22
      2 183.60.136.230
      2 117.25.148.119
      1 23.224.186.37
      1 222.186.59.201
      1 161.35.151.45
```