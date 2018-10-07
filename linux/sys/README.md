> 内存计算

### 查看内存的命令

    free – 一个在 Linux 上查看内存用量统计（可用和已用）的标准工具
    smem – Linux 内存报告/统计工具
    vmstat – 一个好用的用于虚拟内存统计的标准工具
    top – 功能比较齐全

### # free  

    ➜  ~ free -h
                  total        used        free      shared  buff/cache   available
    Mem:           3.9G        835M        2.5G         19M        533M        2.7G
    Swap:            0B          0B          0B


total: 总内存 = ( used+free+buff/cache )

used: 已经使用的内存

free: 空闲的内存数

shared: 多个进程共享的内存总额

buffers Buffer：缓存内存数

available: 可用内存 = ( free+ buffer/cache)  


### # free 与 available

> [参考](https://www.imooc.com/article/26314)

在 free 命令的输出中，有一个 free 列，同时还有一个 available 列。这二者到底有何区别？
free 是真正尚未被使用的物理内存数量。至于 available 就比较有意思了，它是从应用程序的角度看到的可用内存数量。Linux 内核为了提升磁盘操作的性能，会消耗一部分内存去缓存磁盘数据，就是我们介绍的 buffer 和 cache。所以对于内核来说，buffer 和 cache 都属于已经被使用的内存。当应用程序需要内存时，如果没有足够的 free 内存可以用，内核就会从 buffer 和 cache 中回收内存来满足应用程序的请求。所以从应用程序的角度来说，available  = free + buffer + cache。请注意，这只是一个很理想的计算方式，实际中的数据往往有较大的误差。

CPU 负载
---
[参考:维基百科](https://en.wikipedia.org/wiki/Load_(computing))

- uptime the system reliability and load average
- top for an overall system view
- vmstat vmstat reports information about runable or blocked processes, memory, paging, block I/O, traps, and CPU.
- htop interactive process viewer
- dstat [1] helps correlate all existing resource data for processes, memory, paging, block I/O, traps, and CPU activity.
- iftop interactive network traffic viewer per interface
- nethogs interactive network traffic viewer per process
- iotop interactive I/O viewer - iotop homepage
- iostat for storage I/O statistics
- netstat for network statistics
- mpstat for CPU statistics
- tload load average graph for terminal
- xload load average graph for X
- /proc/loadavg text file containing load average

网络连接数
-----
    
    ss -s
    netstat -n | awk '/^tcp/ {++S[$NF]} END { for(a in S) print(a,S[a])}'
