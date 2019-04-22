> SSH是服务器管理中常用工具，使用如下配置可最大保护服务器安全。

### SSH配置
```
1. Port 不要使用默认端口。
2. PermitRootLogin no        禁止root远程登录。
3. PermitEmptyPasswords no   禁止空密码登录。
4. PasswordAuthentication no 禁止使用密码方式登录。
5. GSSAPIAuthentication no
```

### 防火墙配置
> 可根据来源IP限制登录。

### 感谢：
https://newtoypia.blogspot.com/2017/04/watertight-ssh.html
