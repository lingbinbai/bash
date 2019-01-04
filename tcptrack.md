## 概述
> tcptrack 可以展示TCP连接的状态，它在一个给定的网络端口上进行监听。监控它们的状态并展示出排序且不断更新的列表。

## 在centos6系统中安装过程如下

wget http://ftp.tu-chemnitz.de/pub/linux/dag/redhat/el6/en/x86_64/rpmforge/RPMS/tcptrack-1.4.0-1.el6.rf.x86_64.rpm
rpm -ivh tcptrack-1.4.0-1.el6.rf.x86_64.rpm

## 使用示例
1. 监控p4p1网口下所有连接
tcptrack -i p4p1

2. 监控80端口产状态
tcptrack -i p4p1 port 80

> tcptrack 需要以 root 权限或超级用户身份来运行。
### 资料来源
> https://linux.cn/article-5435-4.html
