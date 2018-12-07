### 测试网页打开速度

```
curl -o /dev/null -s -w %{time_namelookup}:%{time_connect}:%{time_starttransfer}:%{time_total} http://www.baidu.com
```

> 0.037 : 0.042 : 2.692 : 2.765
解析     建立连接  传输   总
