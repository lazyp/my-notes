引用 http://jaseywang.me/2012/10/15/scp-出现-stalled-的分析/

scp 出现 stalled 的分析
Posted on October 15, 2012
在使用 scp 进行一些大文件传输时，会出现 stalled 的情况，不外乎下面两个原因。

scp 对带宽的使用是贪婪的，因此有多少的带宽他就会使用多少(实际情况很复杂，并不全是贪婪的情况，也不是有多少用多少)，但是如果一旦由于网络设备或者防火墙造成了一些延时，就会导致此次传输出现 TCP stalled。对此，可以通过限速解决，以 200Kbit/s 的速度进行传输:
$ scp -l 200 file dst:

另外还有个次要原因，可能是由于 Linux 下的 SACK 的造成。一般开启限速功能应该就能解决绝大多数的情况了。SACK 是什么请看这里。
要使用 TCP option 中的 SACK，需要两端都支持。

根据这篇文章的描述，在局域网或者低延迟的网络中，就完全没有必要开启 SACK options 了，另外在很小的带宽下，比如 1Mbps 的情况下，同样没有必要开启这个选项。该选项可以在 "high bandwidth, lossy (or high delay)" 的情况下开启。因此出现 stalled 的情况一般都是在客户从公网连接某台服务器，带宽一般都是比较小的，瓶颈带宽在客户端这边，而不大可能是两台同一链路(连在同一台交换机)的服务器之间的数据传输。因此关闭 SACK 会比较有利传输:
> echo 0 > /proc/sys/net/ipv4/tcp_sack

ref: http://daybydaylinux.blogspot.jp/2011/02/scp-stalled-during-big-files-transfer.html


------------------


When transferring large files(for example mksysb images) usingscp through a firewall, the scp connection stalls.

Cause:
The reason for scp to stall, is because scp greedily grabs asmuch bandwith of the network as possible when it transfers files,any delay caused by the network switch of the firewall can easilymake the TCP connection stalled.

Solution:
There’s a solution to this problem: Add “-l 8192″ to the scpcommand.

Adding the option “-l 8192″ limits the scp session bandwith upto 8192 Kbit/second, which seems to work safe and fast enough (upto 1 MB/second):
