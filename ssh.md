**ssh登录**

```bash
ssh user@hostname			#user为用户名，hostname为IP地址或域名
ssh user@hostname -p <number>		#登录特定的端口
```



**配置文件（创建文件~/.ssh/config）**

```bash
Host myserver
	HostName IP地址或域名
	User 	 用户名					#登录服务器时可使用别名myserver
```

**密钥登录**

1、输入ssh-keygen然后一直回车即可

2、执行结束后，~/.ssh/目录下会多两个文件：

​	id_rsa：私钥
​	id_rsa.pub：公钥
​	之后想免密码登录哪个服务器，就将公钥传给哪个服务器即可。

​	例如，想免密登录myserver服务器。则将公钥中的内容，复制到myserver中的~/.ssh/authorized_keys文件里即可。

​	也可以使用如下命令一键添加公钥：

​	ssh-copy-id myserver

在本地终端中输入<ssh myserver 'for ((i = 0; i < 10; i ++)) do echo &i; done'>可输出0到9每个各占一行，要用单引号



**scp传文件**

命令格式：<scp source destination>	将source路径下的文件复制到destination中

一次复制多个文件：<scp source1 source2 destination>

复制文件夹：scp -r ~/tmp myserver:/home/acs/  

将本地家目录中的tmp文件夹复制到myserver服务器中的/home/acs/目录下。

scp -r ~/tmp myserver:homework/  将本地家目录中的tmp文件夹复制到myserver服务器中的~/homework/目录下。

scp -r myserver:homework **.**   将myserver服务器中的~/homework/文件夹复制到本地的当前路径下。

指定服务器的端口号：scp -P 22 source1 source2 destination
注意： scp的-r -P等参数尽量加在source和destination之前。

使用scp配置其他服务器的vim和tmux
```
scp ~/.vimrc ~/.tmux.conf myserver:
```



