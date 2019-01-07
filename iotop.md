> iotop命令是一个用来监视磁盘I/O使用状况的top类工具。iotop具有与top相似的UI，其中包括PID、用户、I/O、进程等相关信息。Linux下的IO统计工具如iostat，nmon等大多数是只能统计到per设备的读写情况，如果你想知道每个进程是如何使用IO的就比较麻烦，使用iotop命令可以很方便的查看。

# 安装
### Ubuntu
> apt-get install iotop

### Centos
> yum install iotop

# 选项
-o, --only - 只显示有实际读写I/O的进程或线程，而不是显示所有进程或线程，在交互的时候，可以按下o来切换显示模式
-b, --batch - 非交互模式，通常用于记录I/O使用的脚本中
-n NUM, --iter=NUM - 设置退出前执行的次数，通常在非交互的脚本中使用
-d SEC, --delay=SEC - 刷新间隔时间，默认一秒。也可以使用小数点，例如 1.1秒
-p PID, --pid=PID - 列出要监控的一组进程/线程（默认是所有）
-u USER, --user=USER - 监控的用户列表（默认是所有）
-P, --processes - 只显示进程。
-a, --accumulated - 显示积累的（accumulated）I/O代替带宽。在这个模式下，iotop显示从iotop启动依赖已经完成的I/O进程数量
-k, --kilobytes - 使用KB来显示而不是使用人容易理解的计算单位。这个模式比较适合在脚本中使用iotop。
-t, --time - 在每一行添加一个时间戳
-q, --quiet- 去除头部一些行：这个参数可以设置最多3次来移除头部行：-q列头部只在最初交互显示一次；-qq列头部不显示；-qqq，I/O的总结不显示。

