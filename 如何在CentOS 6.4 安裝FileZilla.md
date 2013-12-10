0. 取得 root 權限
------------------

		$ su - root
		輸入密碼


1. 更新 rpmforge
-----------------

    32bit
    # rpm -Uhv http://apt.sw.be/redhat/el5/en/i386/rpmforge/RPMS/rpmforge-release-0.3.6-1.el5.rf.i386.rpm

		64bit
		# rpm -Uhv http://apt.sw.be/redhat/el6/en/x86_64/rpmforge/RPMS/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm

2. 用 yum 安裝 filezilla
-------------------------

		# yum install filezilla


若不成功可試著安裝下列:
 
    # rpm -Uhv http://fedora.mirrors.pair.com/epel/6/i386/epel-release-6-8.noarch.rpm


再用YUM安裝

    # yum install filezilla
    - See more at: http://www.pimir.net/2013/10/install-filezilla-on-centos-6-4.html#sthash.4oAerco2.dpuf
