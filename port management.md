# Port Management

## `netstat`
`netstat` 命令用于显示各种网络相关信息，如网络连接，路由表，接口状态 (Interface Statistics)，masquerade 连接，多播成员 (Multicast Memberships) 等等。

```sh
Active Internet connections (w/o servers)
Proto  Recv-Q  Send-Q  Local Address            Foreign Address          State
tcp    0       2       210.34.6.89:telnet       210.34.6.96:2873         ESTABLISHED
tcp    296     0       210.34.6.89:1165         210.34.6.84:netbios-ssn  ESTABLISHED
tcp    0       0       localhost.localdom:9001  localhost.localdom:1162  ESTABLISHED
tcp    0       0       localhost.localdom:1162  localhost.localdom:9001  ESTABLISHED
tcp    0       80      210.34.6.89:1161         210.34.6.10:netbios-ssn  CLOSE

Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags Type State I-Node Path
unix 1 [ ] STREAM CONNECTED 16178 @000000dd
unix 1 [ ] STREAM CONNECTED 16176 @000000dc
unix 9 [ ] DGRAM 5292 /dev/log
unix 1 [ ] STREAM CONNECTED 16182 @000000df
```


* `netstat -anp`
* `netstat -ntlp`: 查看当前所有tcp端口 
* `netstat -ntulp | grep 3306`:  查看所有3306端口使用情况

https://www.runoob.com/w3cnote/linux-check-port-usage.html

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMTMyMjAzODFdfQ==
-->