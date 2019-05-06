> ss 命令用来显示处于活动状态的套接字信息。ss命令可以用来获取socket统计信息，它可以显示和netstat类似的内容。但ss的优势在于它能够显示更多更详细的有关TCP和连接状态的信息，而且比netstat更快速更高效。

[详细笔记](http://www.ttlsa.com/linux-command/ss-replace-netstat/)

当服务器的socket连接数量变得非常大时，无论是使用netstat命令还是直接cat /proc/net/tcp，执行速度都会很慢。可能你不会有切身的感受，但请相信我，当服务器维持的连接达到上万个的时候，使用netstat等于浪费 生命，而用ss才是节省时间。


语法
---
    ss(选项)

选项
---
    -h：显示帮助信息；
    -V：显示指令版本信息；
    -n：不解析服务名称，以数字方式显示；
    -a：显示所有的套接字；
    -s: 打印统计概要
    -l：显示处于监听状态的套接字；
    -o：显示计时器信息；
    -m：显示套接字的内存使用情况；
    -p：显示使用套接字的进程信息；
    -i：显示内部的TCP信息；
    -4：只显示ipv4的套接字；
    -6：只显示ipv6的套接字；
    -t：只显示tcp套接字；
    -u：只显示udp套接字；
    -d：只显示DCCP套接字；
    -w：仅显示RAW套接字；
    -x：仅显示UNIX域套接字。
    
实例
---

    # 显示 ICP 连接
    ss -t -a
    # 显示 Sockets 摘要
    ss -s
    # 列出所有打开的网络连接端口
    ss -l
    # 查看进程使用的socket
    ss -pl
    # 找出打开套接字/端口应用程序
    ss -pl | grep 3306
    # 显示所有UDP Sockets
    ss -u -a
    # 显示443端口线程数量
    ss -ant sport = :443  | wc -l
    # 显示tcp 链接情况
    ss  -sn
    