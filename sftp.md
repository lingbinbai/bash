### 1. 安装 sftp

如果要运行sftp服务，则必须在服务器上安装sshd包.使用下边的命令，检查服务器是否已安装sshd包。

```
rpm -qa|grep ssh
```

以下是输出结果，至少应该包含以个包

```
libssh2-1.4.3-10.el7_2.1.x86_64
openssh-7.4p1-13.el7_4.x86_64
openssh-server-7.4p1-13.el7_4.x86_64
openssh-clients-7.4p1-13.el7_4.x86_64
```

### 2.配置sftp

完成sshd安装后，接下来配置sftp. 根据最佳经验，我们建议创建一个用户组和用户，以方便我们管理用户。
首先，让我们创建一个目录，并取名data. 该目录用来存放sftp用户的数据, 所有sftp用户的文件将以子目录的形式，存放于data目录下。

```
mkdir -p /data/sftp
chmod 701 /data
```

创建sftp用户组

```
groupadd sftpusers
```

创建sftp登录用户，并将其添加到sftpuser组

```
useradd -g sftpusers -d /upload -s /sbin/nologin mysftpuser
passwd mysftpuser
```

将/upload目录，置于/data/mysftpuser之下.

```
mkdir -p /data/mysftpuser/upload
chown -R root:sftpusers /data/mysftpuser
chown -R mysftpuser:sftpusers /data/mysftpuser/upload
```

检查新创建的目录

```
[root@localhost ~]# ls -ld /data/
drwx-----x. 5 root root 54 Mar 22 14:29 /data/
```

```
[root@localhost ~]# ls -ld /data/mysftpuser
drwxr-xr-x. 3 root sftpusers 20 Mar 22 14:29 /data/mysftpuser
```

```
[root@localhost ~]# ls -ld /data/mysftpuser/upload
drwxr-xr-x. 2 mysftpuser sftpusers 6 Mar 22 14:29 /data/mysftpuser/upload
```

```
[root@localhost ~]# cat /etc/passwd|grep mysftpuser
mysftpuser:x:1001:1001::/upload:/sbin/nologin
```

配置ssh，运行sftp进程
```
vim /etc/ssh/sshd_config
```

添加下边行到sshd_config末尾

```
Match Group sftpusers
ChrootDirectory /data/%u
ForceCommand internal-sftp
```

修改以下配置文件

```
Subsystem sftp internal-sftp
```


重启ssh 服务

```
service sshd restart
service sshd status
```

### 常见问题

Write failed: Broken pipe  
> 这个问题的原因是ChrootDirectory的权限问题，你设定的目录必须是root用户所有，否则就会出现问题。所以请确保sftp用户根目录的所有人是root, 权限是 750 或者 755。注意以下两点原则：

- 目录开始一直往上到系统根目录为止的目录拥有者都只能是 root，用户组可以不是 root。
- 目录开始一直往上到系统根目录为止都不可以具有群组写入权限 
- 上面2点一定注意，仔细检查。我就是因为这个问题，导致一直有这个问题。仔细检查配置后，解决问题。


### 参考
https://www.howtoforge.com/tutorial/how-to-setup-an-sftp-server-on-centos/
https://blog.51cto.com/fly007/1336156
https://www.cnblogs.com/whatmiss/p/7068772.html
https://blog.csdn.net/moest/article/details/50844834

