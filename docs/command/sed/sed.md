##1. 案例1
####1.准备案例1文件
```shell
cd /tmp
cat /etc/passwd > ./pwd.txt
```
####2.匹配含有ROOT的行，不区分大小写
```shell
grep -i "ROOT" pwd.txt
```
```shell
root@baiduyun:/tmp# grep -i "ROOT" pwd.txt
root:x:0:0:root:/root:/bin/bash
nm-openvpn:x:120:126:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
```
####3.匹配含有root的行，并显示行号
```shell
grep -n "root" pwd.txt

root@baiduyun:/tmp# grep -n "root" pwd.txt
1:root:x:0:0:root:/root:/bin/bash
40:nm-openvpn:x:120:126:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
```
####4. 找出login有关的行
```shell
grep "login" pwd.txt -n
```
```shell
root@baiduyun:/tmp# grep "login" pwd.txt -n
2:daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
3:bin:x:2:2:bin:/bin:/usr/sbin/nologin
4:sys:x:3:3:sys:/dev:/usr/sbin/nologin
...
```
####5. 找出没有login的行
```shell
grep -v -n "login" pwd.txt
```
```shell
root@baiduyun:/tmp# grep -v -n "login" pwd.txt
1:root:x:0:0:root:/root:/bin/bash
5:sync:x:4:65534:sync:/bin:/bin/sync
31:tss:x:111:117:TPM software stack,,,:/var/lib/tpm:/bin/false
33:whoopsie:x:113:120::/nonexistent:/bin/false
42:speech-dispatcher:x:122:29:Speech Dispatcher,,,:/run/speech-dispatcher:/bin/false
45:hplip:x:125:7:HPLIP system user,,,:/run/hplip:/bin/false
47:gnome-initial-setup:x:127:65534::/run/gnome-initial-setup/:/bin/false
48:gdm:x:128:133:Gnome Display Manager:/var/lib/gdm3:/bin/false
```
####6. 同时过滤出root和sync有关的行
```shell
grep -E "root|sync" pwd.txt
```
```shell
root@baiduyun:/tmp# grep -E "root|sync" pwd.txt
root:x:0:0:root:/root:/bin/bash
sync:x:4:65534:sync:/bin:/bin/sync
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
nm-openvpn:x:120:126:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
```
####7. 统计匹配结果的行数
```shell
grep "login" pwd.txt -c
```
```shell
root@baiduyun:/tmp# grep "login" pwd.txt -c
40
```
####8. 只输出匹配的内容
```shell
grep "login" pwd.txt -n -o
```
```shell
root@baiduyun:/tmp# grep "login" pwd.txt -n -o
2:login
3:login
4:login
6:login
7:login
8:login
9:login
10:login
11:login
12:login
13:login
14:login
15:login
16:login
17:login
18:login
19:login
20:login
21:login
22:login
23:login
24:login
25:login
26:login
27:login
28:login
29:login
30:login
32:login
34:login
35:login
36:login
37:login
38:login
39:login
40:login
41:login
43:login
44:login
46:login
```
####9. 完整匹配，字符串精确匹配整个单词
```shell
grep "root" pwd.txt -w
```
```shell
root@baiduyun:/tmp# grep "root" pwd.txt -w
root:x:0:0:root:/root:/bin/bash
```
####10. 过滤掉空白行和注释行（配置文件常用！）
```shell
grep -Ev "^#|^$" /etc/ssh/ssh_config
```
```shell
#配置文件行数是52行
root@baiduyun:/tmp# cat /etc/ssh/ssh_config|wc -l
52

# 过滤掉注释行和空白行后的配置文件
root@baiduyun:/tmp# cat /etc/ssh/ssh_config|grep -Ev "^#|^$"
Include /etc/ssh/ssh_config.d/*.conf
Host *
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
```
##2. 案例2
####1. 准备案例2文件
```shell
root@baiduyun:/tmp# vim cp.txt
root@baiduyun:/tmp# cat -n cp.txt
     1  I am chupeng.
     2
     3  How are you?
     4  My website is https://chupeng.site
     5  bye.
```     
####2.匹配site结尾的行¶
```shell
grep -i -n "site$" cp.txt

# 注意：Linux中所有文件的结尾都有一个$符号，可以使用cat -A查看验证！
```
```shell
root@baiduyun:/tmp# grep -i -n "site$" cp.txt
4:My website is https://chupeng.site
```
####3. 输出以“.”结尾的行，注意使用转义符！
```shell
grep -i -n ".$" cp.txt  #错误
grep -i -n "\.$" cp.txt
```
```shell
# 不加转义符，“.”就是正则匹配中代表一个字符！
root@baiduyun:/tmp# grep -i -n ".$" cp.txt
1:I am chupeng.
3:How are you?
4:My website is https://chupeng.site
5:bye.

# 加上转义符才能输出结果！
root@baiduyun:/tmp# grep -i -n "\.$" cp.txt
1:I am chupeng.
5:bye.
```
####4. 找出i出现0次或多次
```shell
grep "i*" cp.txt -n
```
```shell
root@baiduyun:/tmp# grep "i*" cp.txt -n
1:I am chupeng.
2:
3:How are you?
4:My website is https://chupeng.site
5:bye.
# 为什么全文都匹配到了呢？因为“*”前一个字符出现0次的也匹配！也就是匹配所有！
# 如果输出包含i的，可以只加i，或者i.*
root@baiduyun:/tmp# grep "i" cp.txt -n
4:My website is https://chupeng.site
root@baiduyun:/tmp# grep "i.*" cp.txt -n
4:My website is https://chupeng.site
```
####5. 匹配非空行
```shell
grep ".*" cp.txt -n # 错误
grep -v "^$" cp.txt -n
```
```shell
root@baiduyun:/tmp# grep ".*" cp.txt -n
1:I am chupeng.
2:
3:How are you?
4:My website is https://chupeng.site
5:bye.
root@baiduyun:/tmp# grep -v "^$" cp.txt -n
1:I am chupeng.
3:How are you?
4:My website is https://chupeng.site
5:bye.
```
####6.贪婪匹配
```shell
grep ".*e" cp.txt
```
```shell
root@baiduyun:/tmp# grep ".*e" cp.txt
I am chupeng.
How are you?
My website is https://chupeng.site
bye.
```
####7. 匹配字符
```shell
grep '[a-z]' cp.txt # 匹配含有小写字母的行
grep '[A-Z]' cp.txt # 匹配含有大写字母的行
```
```shell
root@baiduyun:/tmp# grep '[a-z]' cp.txt
I am chupeng.
How are you?
My website is https://chupeng.site
bye.
root@baiduyun:/tmp# grep '[A-Z]' cp.txt
I am chupeng.
How are you?
My website is https://chupeng.site
```
####8. 匹配所有大小写字符和数字
```shell
grep '[a-zA-Z0-9]' cp.txt
```
```shell
root@baiduyun:/tmp# grep '[a-zA-Z0-9]' cp.txt
I am chupeng.
How are you?
My website is https://chupeng.site
bye.
```
####9. 只显示被匹配到的关键字
```shell
grep -o 'a' cp.txt
```
```shell
root@baiduyun:/tmp# grep -o 'a' cp.txt
a
a
```
####10. +使用:匹配字母出现一次或多次的行
```shell
grep -E 'c+' cp.txt
```
```shell
root@baiduyun:/tmp# grep -E 'c+' cp.txt
I am chupeng.
My website is https://chupeng.site
```
####11. ？使用：o字母出现0次或1次的行
```shell
vim cp2.txt
gd
god
good
goooood
gld
glad
glaad
gllaad
```
```shell
grep -E 'go?d' cp2.txt
    # 只能匹配2种结果：gd，god
```    
```shell
root@baiduyun:/tmp# grep -E 'go?d' cp2.txt
gd
god
```
####12. |使用：找出深度为3层种所有的txt文件，且名字包含a或者b的txt文件
```shell
find / -maxdepth 3 -name "*.txt" |grep -i -E "a|b"
```
```shell
root@baiduyun:/tmp# find / -maxdepth 3 -name "*.txt" |grep -i -E "a|b"
/boot/grub/gfxblacklist.txt
/service/qqemail/requirements.txt
/etc/X11/rgb.txt
```
####13. 找出包含good和glad的行
```shell
grep -E 'good|glad' cp2.txt
grep -E 'g(oo|la)d' cp2.txt
```
```shell
root@baiduyun:/tmp# grep -E 'good|glad' cp2.txt
good
glad
root@baiduyun:/tmp# grep -E 'g(oo|la)d' cp2.txt
good
glad
```
####14. 匹配字母l和e之间有2个其他字母的单词的行
```shell
root@baiduyun:/tmp# vim cp3.txt
root@baiduyun:/tmp# cat cp3.txt
love
like
look
lie
lee
```
```shell
grep 'l..e' cp3.txt # 匹配到like、love
```
```shell
root@baiduyun:/tmp# grep 'l..e' cp3.txt
love
like
```
##3. 案例3
####1. 匹配字母a最少出现1次，最多出现3次的行
```shell
grep -E "o{1,3}" cp2.txt
```
```shell
root@baiduyun:/tmp# grep -E "o{1,3}" cp2.txt
god
good
goooood
```
####2. 只输出匹配内容
```shell
grep -E -o "o{1,3}" cp2.txt
```
```shell
root@baiduyun:/tmp# grep -E -o "o{1,3}" cp2.txt
o
oo
ooo
oo
```
####3. 输出a连续出现4次以上的行
```shell
grep -E -o "o{4,}" cp2.txt
```
```shell
root@baiduyun:/tmp# grep -E  "o{4,}" cp2.txt
goooood
```
####4. 输出a输出4次以下的行
```shell
grep -E -o "o{,4}" cp2.txt
```
```shell
root@baiduyun:/tmp# grep -E "o{,4}" cp2.txt
gd
god
good
goooood
gld
glad
glaad
gllaad
```