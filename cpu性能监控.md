```
#!/bin/bash
#yum install sysstat.x86_64
#sar -o 2 3


if [ $# -ne 1 ]; then
    echo -1
    exit 0
fi

host=$1
cpuidle="100"

if [ $host = "localhost" ]; then
    cpuidle=`sar -u | tail -1 | awk '{print $8}' | awk -F"." '{print $1}'`
else
    #TOTAL_MEM=` ssh $host "cat /proc/meminfo | egrep -w MemTotal" | awk '{print \$2}' `
    cpuidle=`ssh $host "sar -u" | tail -1 | awk '{print $8}' | awk -F"." '{print $1}'`
fi
echo $cpuidle
```
