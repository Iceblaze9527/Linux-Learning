# temp

* `alias` : give certain command an alias in one session (expired after reboot)
* `unalias` : opposite of alias
* `env` : show environment variable
* `echo $ENV_VAR_NAME` : show value of certain environment variable on stdout
* `history` : display history command list

* `netstat -ntlp`: 查看当前所有tcp端口 
* `netstat -ntulp | grep 3306`:  查看所有3306端口使用情况

## 软链接 `ln`
* `ln -s src_path dst_path`: 创建软链接
* `rm -rf dst_path`: 删除软链接
* `ln –snf new_src_path dst_path`: 修改软链接

### 参数含义
* `-n`: 把符号链接视为一般目录
* `-s` 软链接(符号链接)

https://www.runoob.com/w3cnote/linux-check-port-usage.html

A Linux system is divided into three main parts:

-   Hardware - This includes all the hardware that your system runs on as well as memory, CPU, disks, etc.
-   Linux Kernel - As we discussed above, the kernel is the core of the operating system. It manages the hardware and tells it how to interact with the system.
-   User Space - This is where users like yourself will be directly interacting with the system.

The shell is basically a program that takes your commands from the keyboard and sends them to the operating system to perform.

```sh
(base) yutongx@simons-1:~$ date
Fri Jul 17 19:57:18 PDT 2020
(base) yutongx@simons-1:~$ whoami
yutongx
(base) yutongx@simons-1:~$ echo hello
hello
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDUzMzkzODMsMzczMzU0MTI5XX0=
-->