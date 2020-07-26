# [SSH for Remote Access](https://medium.com/@apbetahouse45/how-to-run-jupyter-notebooks-on-remote-server-part-1-ssh-a2be0232c533)

## 1. Access Remote Server using SSH
As you may or may not know, when you connect to your remote server and you get the shell access, it is done through ssh. There are two ways general ways to authenticate with the remote server:

-   Using password
-   Using Pub/Private Keys

On Unix, you might do something like `ssh username@remote_host` and then you have to enter a password (password authentication) or you use your private key (which is the more secure method)

## 2. [Access Jupyter Notebook Remotely via SSH Tunnel](https://medium.com/@shahnewazk/connecting-to-a-jupyter-notebook-on-a-remote-linux-machine-277cef04abb7)

```sh
username_1@local_host $ ssh -N -L localhost:port_num_1:localhost:port_num_2 username_2@remote_host
```

On the local machine browser load `localhost:port_num_1` and the `Jupyter Notebook` from your remote machine will load out as expected.

### 2.1 What is SSH Tunneling?

![](https://miro.medium.com/max/2118/1*uGLPZIeLPkvvaRkVG1-tkw.png)
This is also known as port forwarding. What this means is that you setup a network tunnel (a connection for data to flow) from a local point to remote point. Any network request you send to port `localhost:port_num_1` in your current system will be automatically forwarded to `localhost:port_num_2` from the remote system.

### 2.2 break down of the ssh options
#### `-N` Do not execute a remote command
This is useful for just forwarding ports

Note that running the SSH tunnel with `-N` will not log any outputs, as long as you do not get an error this means you have established a tunnel.

#### `-L local_socket:remote_socket` 
Specifies that connections to the given TCP port or Unix socket on the local (client) host are to be forwarded to the given host and port, or Unix socket, on the remote side. This works by allocating a socket to listen to either a TCP port on the local side, optionally bound to the specified bind_address, or to a Unix socket. Whenever a connection is made to the local port or socket, the connection is forwarded over the secure channel, and a connection is made to either host port hostport, or the Unix socket remote_socket, from the remote machine.

Port forwardings can also be specified in the configuration file. Only the superuser can forward privileged ports. IPv6 addresses can be specified by enclosing the address in square brackets.

By default, the local port is bound in accordance with the GatewayPorts setting. However, an explicit bind_address may be used to bind the connection to a specific address. The bind_address of “localhost” indicates that the listening port be bound for local use only, while an empty address or ‘*’ indicates that the port should be available from all interfaces.

## 3. [SSH Constant Connection on Mac](http://bluebiu.com/blog/linux-ssh-session-alive.html)
### 3.1 Causes
1. 服务器存在防火墙，会关闭超时空闲连接，或设置了关闭超时空闲连接。
2. 客服端和服务器之间存在路由器，路由器也可能带有防火墙，会关闭超时空闲连接。
3. 客服端存在防火墙，会关闭超时空闲连接。

#### One-time Solution
`ssh -o ServerAliveInterval=30 username@remote_host`

### 3.2 Solutions from Server (Not Recommended, thus not tested)
1. `TCPKeepAlive yes`: 表示TCP保持连接不断开
2. `ClientAliveInterval 300`: 指定服务端向客户端请求消息的时间间隔，单位是秒，默认是0，不发送。设置个300表示5分钟发送一次（注意，这里是服务端主动发起），然后等待客户端响应，成功，则保持连接。
3. `ClientAliveCountMax 3`: 指服务端发出请求后客户端无响应则自动断开的最大次数。使用默认给的3即可。
4. `sudo /etc/init.d/ssh restart`: 重启sshd服务生效

#### Note
1. `TCPKeepAlive`必须打开，否则直接影响后面的设置
2. `ClientAliveInterval`设置的值要小于各层防火墙的最小值，不然，也就没用了。

### 3.3 Solutions from Mac Client (Recommended)
* for global: `vim /etc/ssh/ssh_config`
* for user: `vim ~/.ssh/config`

```sh
Host host_name: 表示需要启用该规则的服务端（域名或ip）
	User username
	HostName remote_host
	IdentityFile id_rsa_file
	TCPKeepAlive yes
	ServerAliveInterval 60: 表示每60秒去给服务端发起一次请求消息（这个设置好就行了）
	ServerAliveCountMax 3: 表示最大连续尝试连接次数（这个基本不用设置）
	IPQoS lowdelay throughput: MacOS 需要增加，原因在于Qos检测命令不被对端支持，导致连接丢失
```

同时，对于超长时间的SSH监控，需要设置屏幕关闭时不要让电脑休眠，否则依旧会断开

## 4. SSH Key Generation on Unix/Linux
1. `$ cd ~/.ssh`: open user dir
2. `$ ssh-keygen -t rsa -C "email@example.com"`: this would generate two files: `id_rsa` (private key) and `id_rsa.pub` (public key)
3. `$ cat id_rsa.pub`: get public key

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTk1OTUzMDkzLDM3MTE2MjE0N119
-->