# temp
A Linux system is divided into three main parts:

-   Hardware - This includes all the hardware that your system runs on as well as memory, CPU, disks, etc.
-   Linux Kernel - As we discussed above, the kernel is the core of the operating system. It manages the hardware and tells it how to interact with the system.
-   User Space - This is where users like yourself will be directly interacting with the system.

The shell is basically a program that takes your commands from the keyboard and sends them to the operating system to perform.

## 一些命令
* `date`: 显示当前日期和时间
* `whoami`: 显示当前用户
* `alias` : give certain command an alias in one session (expired after reboot)
* `unalias` : opposite of alias
* `env` : show environment variable
* `echo $ENV_VAR_NAME` : show value of certain environment variable on stdout
* `history` : display history command list
* `cat /proc/uptime`

2.查看/proc/uptime文件计算系统启动时间  

输出: 5113396.94 575949.85  
第一数字即是系统已运行的时间5113396.94 秒，运用系统工具date即可算出系统启动时间

代码: [全选](http://bbs.freesinno.com/viewtopic.php?t=66)

`date -d "$(awk -F. '{print $1}' /proc/uptime) second ago" +"%Y-%m-%d %H:%M:%S"`

  
输出: 2008-11-09 11:50:31  
  
3.查看/proc/uptime文件计算系统运行时间




## 软链接 `ln`
* `ln -s src_path dst_path`: 创建软链接
* `rm -rf dst_path`: 删除软链接
* `ln –snf new_src_path dst_path`: 修改软链接

### 参数含义
* `-n`: 把符号链接视为一般目录
* `-s`: 软链接(符号链接)


* `netstat -ntlp`: 查看当前所有tcp端口 
* `netstat -ntulp | grep 3306`:  查看所有3306端口使用情况

https://www.runoob.com/w3cnote/linux-check-port-usage.html

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjY0MDQzMTksMzczMzU0MTI5XX0=
-->