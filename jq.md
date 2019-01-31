#comment : 解析json

### 安装jq工具

#### linux平台
- jq 1.5 is in the official Debian and Ubuntu repositories. Install using sudo apt-get install jq.
- jq 1.5 is in the official Fedora repository. Install using sudo dnf install jq.
- jq 1.4 is in the official openSUSE repository. Install using sudo zypper install jq.
- jq 1.5 is in the official Arch repository. Install using sudo pacman -Sy jq.


#### mac
- Use Homebrew to install jq 1.5 with brew install jq.

#### FreeBSD
- Use FreshPorts to install jq 1.4 with pkg install jq.

#### Solaris
- pkgutil -i jq in OpenCSW for Solaris 10+, Sparc and x86.

#### Windows
- Use Chocolatey NuGet to install jq 1.5 with chocolatey install jq.

```
基本格式：
jq [参数列表]  ‘过滤条件’ 文件名或标准输入
例：
jq -c ‘.foo’ a.json
或：
cat a.json | jq -c ‘.foo’
```


### 常见用法
#### 格式化JSON 
```
cat json_raw.txt | jq .
```

#### 根据key获取value
```
jq '.key'
```
> 解析不存在的元素，会返回null

#### 嵌套解析
```
cat json_raw.txt | jq '.location.state'
"California"
```

#### has是用来是判断是否存在某个key：
```
cat json_raw.txt | jq 'has("name")'
true
 
cat json_raw.txt | jq 'has("noexisted")'
false
```



参考:http://justcode.ikeepstudying.com/2018/02/shell%EF%BC%9A%E6%97%A0%E6%AF%94%E5%BC%BA%E5%A4%A7%E7%9A%84shell%E4%B9%8Bjson%E8%A7%A3%E6%9E%90%E5%B7%A5%E5%85%B7jq-linux%E5%91%BD%E4%BB%A4%E8%A1%8C%E8%A7%A3%E6%9E%90json-jq%E8%A7%A3%E6%9E%90-json/
