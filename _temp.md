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

## 时间管理
* `who -b`: 查看最后一次系统启动的时间
* `who -r`: 查看当前系统运行时间
* `last reboot`: Linux系统历史启动的时间

### `cat /proc/uptime`
* 第一列输出的是系统启动到现在的时间（以秒为单位）
* 第二列输出的是系统空闲的时间（以秒为单位）

在SMP系统里，系统空闲的时间有时会是系统运行时间的几倍，这是怎么回事呢？  
因为系统空闲时间的计算，是把SMP算进去的，就是所你有几个逻辑的CPU（包括超线程）。

系统的空闲率(%) = num2/(num1*N) 其中N是SMP系统中的CPU个数。

从上面我的一台机器上的数据可知，  
本机启动到现在的时间长度为：6447032.12 seconds = 74.6 days  
空闲率为:48185264.69/(6447032.12*8)=93.4%

系统空闲率越大，说明系统比较闲，可以加重一些负载；而系统空闲率很小，则可能考虑升级本机器硬件或者迁移部分负载到其他机器上。


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
eyJoaXN0b3J5IjpbLTExNDcwMTU0OTksMzczMzU0MTI5XX0=
-->