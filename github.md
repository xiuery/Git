
## github
本文介绍如何使用git操作github

> 两种方式，但是无论哪种方式都要首先创建ssh key

### 1.创建ssh key
在指定path下生成密匙文件，拷贝id_rsa.pub内容到github.com的SSH KEY中
> 如果自定义了ssh-key存放的路径，必须去修改ssh的配置文件
```
$ ssh-keygen -t rsa -C "email"
path
pwd
pwd again
```

### 2.clone项目
#### 2.1 克隆github项目到本地
```
git clone https://github.com/xiuery/Svn.git
or
git clone git@github.com:xiuery/Svn.git
```

#### 2.2 可以通过以下命令查看或操作远程仓库
```
git remote
git remote -v
git remote rm 别名
```

#### 2.3 push到github
```
git add file
git commit -m ""
git push -u origin master
```

#### 2.4 更新本地代码
```
git fetch
git merge
```