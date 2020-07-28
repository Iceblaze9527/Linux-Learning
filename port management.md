# Undefined

## [`netstat`](https://www.cnblogs.com/ggjucheng/archive/2012/01/08/2316661.HTML)
`netstat` 命令用于显示各种网络相关信息，如网络连接，路由表，接口状态 (Interface Statistics)，masquerade 连接，多播成员 (Multicast Memberships) 等等。

### 输出信息
```sh
Active Internet connections (w/o servers)
Proto  Recv-Q  Send-Q  Local Address            Foreign Address          State
tcp    0       2       210.34.6.89:telnet       210.34.6.96:2873         ESTABLISHED
tcp    296     0       210.34.6.89:1165         210.34.6.84:netbios-ssn  ESTABLISHED
tcp    0       0       localhost.localdom:9001  localhost.localdom:1162  ESTABLISHED
tcp    0       0       localhost.localdom:1162  localhost.localdom:9001  ESTABLISHED
tcp    0       80      210.34.6.89:1161         210.34.6.10:netbios-ssn  CLOSE

Active UNIX domain sockets (w/o servers)
Proto  RefCnt  Flags  Type    State      I-Node  Path
unix   1       [ ]    STREAM  CONNECTED  16178   @000000dd
unix   1       [ ]    STREAM  CONNECTED  16176   @000000dc
unix   9       [ ]    DGRAM   5292       /dev/log
unix   1       [ ]    STREAM  CONNECTED  16182   @000000df
```

- `Active Internet connections`: 有源TCP连接
	- `Recv-Q` 和 `Send-Q`: 接收队列和发送队列。这些数字一般都应该是0。如果不是则表示软件包正在队列中堆积。这种情况只能在非常少的情况见到。
- `Active UNIX domain sockets`: 有源Unix域套接口(和网络套接字一样，但是只能用于本机通信，性能可以提高一倍)。  
	- `Proto`: 显示连接使用的协议
	- `RefCnt`: 表示连接到本套接口上的进程号
	- `Types`: 显示套接口的类型
	- `State`: 显示套接口当前的状态
	- `Path`: 表示连接到套接口的其它进程使用的路径名

### 参数
- `-a (all)`: 显示所有选项，默认不显示LISTEN相关  
- `-l`: 仅列出有在 Listen (监听) 的服务状态
- `-n`: 拒绝显示别名，能显示数字的全部转化成数字
- `-p`: 显示建立相关链接的程序名   
- `-t (tcp)`: 仅显示tcp相关选项  
- `-u (udp)`: 仅显示udp相关选项  

提示：LISTEN和LISTENING的状态只有用`-a`或者`-l`才能看到


## `lsof`
`lsof(list open files)`是一个列出当前系统打开文件的工具。

```sh
lsof -i:8080 查看8080端口占用
lsof abc.txt：显示开启文件abc.txt的进程 
lsof -c abc：显示abc进程现在打开的文件 
lsof -c -p 1234：列出进程号为1234的进程所打开的文件 
lsof -g gid：显示归属gid的进程情况 
lsof +d /usr/local/：显示目录下被进程开启的文件 
lsof +D /usr/local/：同上，但是会搜索目录下的目录，时间较长 
lsof -d 4：显示使用fd为4的进程 
lsof -i -U：显示所有打开的端口和UNIX domain文件
```

## 时间管理
* `who -b`: 查看最后一次系统启动的时间
* `who -r`: 查看当前系统运行时间
* `last reboot`: Linux系统历史启动的时间

### `cat /proc/uptime`
* 第一列（`num1`）输出的是系统启动到现在的时间（以秒为单位）
* 第二列（`num2`）输出的是系统空闲的时间（以秒为单位）

在SMP系统里，系统空闲的时间有时会是系统运行时间的几倍，这是因为系统空闲时间的计算是把SMP算进去的，就是说你有几个逻辑的CPU（包括超线程）。

`系统的空闲率(%) = num2/(num1*N)， 其中N是SMP系统中的CPU个数。`

系统空闲率越大，说明系统比较闲，可以加重一些负载；而系统空闲率很小，则可能考虑升级本机器硬件或者迁移部分负载到其他机器上。


## 软链接 `ln`
* `ln -s src_path dst_path`: 创建软链接
* `rm -rf dst_path`: 删除软链接
* `ln –snf new_src_path dst_path`: 修改软链接

### 参数含义
* `-n`: 把符号链接视为一般目录
* `-s`: 软链接(符号链接)
<!--stackedit_data:
eyJoaXN0b3J5IjpbODU5ODk4MTgyXX0=
-->