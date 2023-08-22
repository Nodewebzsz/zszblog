#Linux命令简介
##1. 说明
```
1.Linux与windows最大的区别就是，Linux是命令行终端（当然也有图形界面，如ubuntu），windows是图形界面终端！
  Linux界面，就像在windows中打开cmd后呈现的画面一样！
  在Linux中，鼠标基本上没用（可能复制内容还会用到！），都是靠命令操作！
  linux命令就像windows的鼠标操作一样，熟悉后甚至比鼠标操作更快捷方便！
  所以Linux命令是最基础的东西，Linux上的所有操作基本上都是通过命令来实现的！
  对于从windows转到Linux来说，刚开始可能不适应，所以需要多敲命令来熟悉。
  但是随着经常使用Linux会发现，其实命令也没啥，
  就算某个命令忘记具体用法了，可以使用帮助命令，甚至可以百度查找用法啊，
  当然最起码最常用的命令还是得会的，哈哈
```
##2. 大纲
```
帮助命令
  man cmd
  info cmd
  cmd --help

常用命令
  pwd
  ls
  cd
  cp
  mv
  mkdir 
  touch
  su
  sudo
  date
  cat
  head
  tail
  cut
  sort
  uniq
  wc
  tr
  stat
  find
  file
  xargs
  alias
  ln
  readlink
  echo
  whereis
  which
  ssh
  hostname
  hostnamectl

  md5sum
  dos2unix
  tr
  tee

文件查看命令
  cat
  tac
  more
  less
  head
  tail

压缩解压命令
  tar
  zip
  unzip
  gzip

磁盘管理命令
  mount
  umount
  du
  df
  fdisk
  mkfs

用户管理命令
  useradd
  usermod
  userdel
  passwd
  chpasswd
  chage
  id
  su
  sudo
  visudo
  who
  w
  id
  whoami
  last

权限管理命令
  chmod
  chown
  chgrp
  chattr
  umask

进程管理命令
  ps
  pstree
  kill
  killall
  top
  htop
  glances
  nohup
#  &
  systemctl
  service

网络管理命令
  ifconfig
  ip
  route
  netstat
  ss
  telnet
  ping
  nc
  nslookup
  curl
  wget
  tcpdump

系统管理命令
  free
  uptime
  lscpu
  lspci

安装命令
  rpm
  yum
  apt

三剑客（重点）
  grep
  awk
  sed

定时任务命令
  crontab
  at
```
##3. centos7系统安装
```
# 入门
1.安装VMware虚拟机
2.打开VMware，新建虚拟机，安装centos7系统
3.安装xshell等远程连接工具
4.打开工具，ssh连接，开启Linux大门！
# 细节待补充

# 进阶
# 购买云服务器，使用远程工具连接，开始操作
```