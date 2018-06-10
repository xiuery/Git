
## git服务器
本文介绍如何创建自己的git服务器
> 为了方便文件的管理，以下所有的文件创建均在新创建的用户git的home目录下

### 1.为git服务器创建组、用户以及权限文件
```
groupadd git
useradd git -g git 
usermod -s /usr/bin/git-shell git
mkdir /home/git/.ssh
chmod 700 /home/git/.ssh
touch /home/git/.ssh/authorized_keys
chmod 600 /home/git/.ssh/authorized_keys
```
> 有些教程中指定usermod -s /bin/nologin:这会报错(fatal: protocol error: bad line length character: This)

### 2.在客户端创建ssh key
在所需要连接到git服务器的pc上创建ssh-key，并拷贝到git服务器上的authorized_keys文件中

即在1中创建的文件/home/git/.ssh/authorized_keys，每个ssh-key占一行
```
$ ssh-keygen -t rsa
```
> 如果这里修改了path路径或者服务器的ssh默认端口不是22，必须去修改客户端ssh的配置文件

### 3.初始化仓库：
```
mkdir /home/git/gitserve/		            #创建仓库集合，所有的仓库都放在该目录下
mkdir /home/git/gitserve/xiuery 
git init --bare xiuery.git		            #初始化仓库
chown -R git:git /home/git/gitserve/xiuery
```

### 4.服务端连接
到此为止，git服务器就已经创建好了，可以在客服端通过git clone连接git服务器了
```
git clone git@www.example.com:/home/git/gitserve/xiuery/xiuery.git
```

### 5.如果git服务器ssh默认端口被修改，如何连接git服务器

- 修改客户端ssh配置文件中端口号：
```
git clone git@www.example.com/home/git/gitserve/xiuery/xiuery.git
```

- 不修改ssh配置文件
```
git clone ssh://git@www.example.com:88888/home/git/gitserve/xiuery/xiuery.git
```