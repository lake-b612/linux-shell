# 实训：Linux 常用命令

## 1.实训目的及内容

(1)掌握Linux各类命令的使用方法。

(2)熟悉Linux操作环境。

## 2.实训环境

(1)一台已经安装好Linux操作系统的主机，并且已经配置好基本的TCP/IP参数，能够通过网络连接局域网或远程的主机。

(2)一台Linux服务器，能够提供FTP、Telnet和SSH连接。

## 3.实训练习

### (1)文件和目录类命令。

- 启动计算机，利用root用户登录到系统，进入字符提示界面。
![[Pasted image 20261004162635.png]]
- 用pwd命令查看当前所在的目录。
![[Pasted image 20261004162926.png]]
- 用ls命令列出此目录下的文件和目录。
![[Pasted image 20261004163008.png]]
- 用-a选项列出此目录下包括隐藏文件在内的所有文件和目录。
![[Pasted image 20261004163149.png]]
- 用man命令查看ls命令的使用手册。
man ls
![[Pasted image 20261004163436.png]]

- 在当前目录下创建测试目录test。
- 利用ls命令列出文件和目录，确认test目录创建成功。

![[Pasted image 20261004164148.png]]
- 进入test目录，利用pwd命令查看当前工作目录。
![[Pasted image 20261004164310.png]]
- 利用touch命令在当前目录创建一个新的空文件newfile。
![[Pasted image 20261004164444.png]]
- 利用cp命令复制系统文件/etc/profile到当前目录下。
![[Pasted image 20261004165541.png]]
- 复制文件profile到一个新文件profile.bak作为备份。
![[Pasted image 20261004165929.png]]
- 用ll命令以**长格式**列出**当前目录下的所有文件**，注意**比较每个文件的长度和创建时间的不同**。
![[Pasted image 20261004171236.png]]
- 用less命令分屏查看文件profile的内容，注意练习less命令的各个子命令，例如b、p、q等并对then关键字进行查找。
![[Pasted image 20261004171922.png]]
- 用grep命令在profile文件中对关键字then进行查询，并与上面的结果比较。
![[Pasted image 20261004172623.png]]
- 给文件profile创建一个符号链接lnsprofile和一个硬链接lnhprofile。
- 以长格式显示文件profile、lnsprofile和lnhprofile的详细信息。注意比较3个文件链接数的不同。
![[Pasted image 20261004175742.png]]
![[Pasted image 20261004180510.png]]
![[Pasted image 20261004180650.png]]

- 删除文件profile，用长格式显示文件lnsprofile和lnhprofile的详细信息，比较文件lnhprofile的链接数的变化。
![[Pasted image 20261004220046.png]]
- 用less命令查看文件lnsprofile的内容，看看有什么结果。
- 用less命令查看文件lnhprofile的内容，看看有什么结果。
![[Pasted image 20261004220130.png]]
- 删除文件lnsprofile，显示当前目录下的文件列表，回到上层目录。
![[Pasted image 20261004220239.png]]
- 用tar命令把目录test打包。
![[Pasted image 20261004221045.png]]
- 用gzip命令把打好的包进行压缩。
![[Pasted image 20261004221235.png]]
- 把文件test.tar.gz改名为backup.tar.gz。
- 显示当前目录下的文件和目录列表，确认重命名成功。
![[Pasted image 20261004221429.png]]
- 把文件backup.tar.gz移动到test目录下。
- 显示当前目录下的文件和目录列表，确认移动成功。
![[Pasted image 20261004221612.png]]
- 进入test目录，显示目录中的文件列表。
![[Pasted image 20261004221637.png]]
- 把文件backup.tar.gz解包。
![[Pasted image 20261004222158.png]]
- 显示当前目录下的文件和目录列表，复制test目录为testbak目录作为备份。
![[Pasted image 20261004222415.png]]
- 查找root用户自己的主目录下的所有名为newfile的文件。
![[Pasted image 20261004224526.png]]
- 删除test子目录下的所有文件。
![[Pasted image 20261004224732.png]]
- 利用rmdir命令删除空子目录test。
rmdir test
- 回到上层目录，利用rm命令删除目录test和其下所有文件。
![[Pasted image 20261004225057.png]]
### (2)系统信息类命令。

- 利用date命令显示系统当前时间，并修改系统的当前时间。
![[Pasted image 20261004225937.png]]
- 显示当前登录到系统的用户状态。
![[Pasted image 20261004225950.png]]
- 利用free命令显示内存的使用情况。
![[Pasted image 20261004230019.png]]
- 利用df命令显示系统的硬盘分区及使用状况。
![[Pasted image 20261004230150.png]]
- 显示当前目录下的各级子目录的硬盘占用情况。
![[Pasted image 20261004230244.png]]
### (3)进程管理类命令。

#### 使用ps命令查看和控制进程。
- 显示本用户的进程。
- 显示所有用户的进程。
![[Pasted image 20261004231233.png]]
- 在后台运行cat命令。
![[Pasted image 20261004231610.png]]
- 查看进程cat。
![[Pasted image 20261004231742.png]]
- 杀死进程cat。再次查看进程cat，看其是否已被杀死。
1. `ps aux`查看全部进程，管道`|`将输出交给`grep`，`grep cat`筛选含 cat 字符串的进程，快速定位 cat 进程；会附带 grep 自身进程。
2. 杀死进程：先用`pidof`/`ps`获取进程 PID，使用`kill PID`发送终止信号；无法正常终止时使用`kill -9 PID`强制杀死；也可在 top 中按 k 输入 PID 杀死，或者 killall 按进程名杀死。
![[Pasted image 20261004232726.png]]
#### 使用top命令查看和控制进程。

- 用top命令动态显示当前的进程。
![[Pasted image 20261004232824.png]]
- 只显示用户user01的进程(利用u键)。
进入 top 后，直接按键盘 `u`，然后输入用户名：`user01`，回车。
- 利用k键杀死指定进程号的进程。
top 界面，按 `k`，输入要杀死的进程 PID，回车。
按 `q` 退出 top。
#### 挂起和恢复进程。

- 执行命令cat。
- 按Ctrl+Z组合键挂起进程cat。
- 输入jobs命令，查看作业。
- 输入bg，把cat切换到后台执行。
- 输入fg，把cat切换到前台执行。
- 按Ctrl+C组合键结束进程cat。
![[Pasted image 20261004233356.png]]
#### find命令的使用。

- 在/var/lib目录下查找其所有者是games用户的所有文件。
```
find /var/lib -user games

```
- 在/var目录下查找其所有者是root用户的所有文件。
```
find /var -user root

```
- 查找其所有者不是root、bin和student用户的所有文件并用长格式显示。
![[Pasted image 20261007204440.png]]

> `!` 取反；`-ls` 长格式输出，等同于 ls -l 样式

- 查找/usr/bin目录下所有大小超过1000000B的文件并用长格式显示。
```
find /usr/bin -size +1000000c -ls

```

> c 代表字节；`+` 大于；1000000c = 1000000 字节

- 查找/tmp目录下属于student的所有普通文件，这些文件的修改时间为120min以前，查询结果用长格式显示。
```
find /tmp -user student -type f -mmin +120 -ls

```
- 对于查到的上述文件用-ok选项删除。
```
find /tmp -user student -type f -mmin +120 -ok rm {} \;

```
### (4) rpm软件包的管理。

- 查询系统是否安装了软件包squid。
![[Pasted image 20261007210644.png]]
- 如果没有安装，则挂载Linux安装光盘，安装squid软件包。
 1. 创建挂载点
mkdir /mnt/cdrom
 2. 挂载光盘
mount /dev/cdrom /mnt/cdrom
 3. 查找squid包并安装
rpm -ivh /mnt/cdrom/Packages/squid-xxx.rpm
- 卸载刚刚安装的软件包。
rpm -e squid
- 软件包的升级。
rpm -Uvh /mnt/cdrom/Packages/squid-新版本.rpm
- 软件包的更新。
rpm -Fvh /mnt/cdrom/Packages/squid-新版本.rpm
### (5)tar命令的使用。
系统上的主硬盘在使用的时候有可怕的噪声，但是它上面存在有价值的数据。该系统在两年半以前备份过，现在决定手动备份少数几个最紧要的文件。/tmp目录可以存储不同磁盘分区的数据，可以将文件临时备份到这个目录。

- 在/home目录里，用find命令定位文件所有者是student的文件，然后将其压缩。
find /home -user student -print | tar -cf /tmp/student.tar -T -
- 保存/etc目录下的文件到/tmp目录下。
tar -cf /tmp/etc.tar /etc
- 列出两个文件的大小。
ls -lh /tmp/student.tar /tmp/etc.tar
- 使用gzip压缩文档。
gzip /tmp/student.tar
gzip /tmp/etc.tar
## 4.实训报告

按要求完成实训报告。