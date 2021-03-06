需要添加的几项内容的解释：

    IPADDR    IP地址
    NETMASK    子网掩码
    NETWORK    网关地址

通常，如果我们想更改主机地址为静态地址或者更改主机名，需要修改的几个文件包括：

    /etc/sysconfig/network			            设置主机名和网络配置
    /etc/sysconfig/network-scripts/ifcfg-eth0	针对特定的网卡进行设置
    /etc/resolv.conf				            设置DNS
    /etc/hosts					                设置指定的域名解析地址
    
一般我们只需要修改网卡的配置文件就可以了，例如我的配置文件如下：

    DEVICE=eth0
    BOOTPROTO=static
    TYPE=Ethernet
    NAME="System etho0"
    BROADCAST=192.168.56.255
    HWADDR=08:00:27:24:F8:9B
    IPADDR=192.168.56.101
    IPV6INIT=yes
    IPV6_AUTOCONF=yes
    NETMASK=255.255.255.0
    NETWORK=192.168.56.1
    ONBOOT=yes
    
设置完成后，重启一下网卡就可以了：service network restart

我们还有一个办法可以实现设置静态IP，那就是通过 ifconfig 这个命令。通常，我们都用它来查看当前网卡的一些信息，同时，他也可以用来进行一些网卡信息的设置。

修改的命令如下：ifconfig eth0 192.168.56.102

但是，这个命令执行后，只能够在当前会话中修改网卡的地址，我们看一下 ifcfg-eth0 的配置文件，仍然是

    # Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE]
    DEVICE=eth0
    ONBOOT=yes
    BOOTPROTO=dhcp
    HWADDR=08:00:27:43:73:2f
也就是说重新启动服务器后，仍然会按照配置文件中的方式进行IP的获取。

所以，如果需要修改IP为静态IP的话，最好的方式还是通过修改配置文件来完成。

*界面操作流程*
--------------------

     System -> Preference -> Network Connections -> System eth0-> edit -> IPv4 Setting 
