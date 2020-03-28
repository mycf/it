[Oracle Database 11g 安装包](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html#11g)

[Oracle Database Preinstallation Tasks](https://docs.oracle.com/cd/E11882_01/install.112/e47689/pre_install.htm#LADBI1085)安装前

```shell
[root@shehuo-db001 yum.repos.d]# wget https://yum.oracle.com/RPM-GPG-KEY-oracle-ol6 -O /etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
--2020-02-22 11:04:19--  https://yum.oracle.com/RPM-GPG-KEY-oracle-ol6
正在解析主机 yum.oracle.com (yum.oracle.com)... 23.1.245.174
正在连接 yum.oracle.com (yum.oracle.com)|23.1.245.174|:443... 已连接。
已发出 HTTP 请求，正在等待回应... 200 OK
长度：1011 [text/plain]
正在保存至: “/etc/pki/rpm-gpg/RPM-GPG-KEY-oracle”

100%[=========================================================>] 1,011       --.-K/s 用时 0s      

2020-02-22 11:04:22 (177 MB/s) - 已保存 “/etc/pki/rpm-gpg/RPM-GPG-KEY-oracle” [1011/1011])

[root@shehuo-db001 yum.repos.d]# gpg --quiet --with-fingerprint /etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpg: 新的配置文件‘/root/.gnupg/gpg.conf’已建立
gpg: 警告：在‘/root/.gnupg/gpg.conf’里的选项于此次运行期间未被使用
pub  2048R/EC551F03 2010-07-01 Oracle OSS group (Open Source Software group) <build@oss.oracle.com>
密钥指纹 = 4214 4123 FECF C55B 9086  313D 72F9 7B74 EC55 1F03

[root@shehuo-db001 yum.repos.d]# wget http://public-yum.oracle.com/public-yum-ol7.repo
--2020-02-22 11:07:10--  http://public-yum.oracle.com/public-yum-ol7.repo
正在解析主机 public-yum.oracle.com (public-yum.oracle.com)... 23.1.245.174
正在连接 public-yum.oracle.com (public-yum.oracle.com)|23.1.245.174|:80... 已连接。
已发出 HTTP 请求，正在等待回应... 200 OK
长度：16402 (16K) [text/plain]
正在保存至: “public-yum-ol7.repo”

100%[=========================================================>] 16,402      --.-K/s 用时 0s      

[root@shehuo-db001 yum.repos.d]# yum install oracle-rdbms-server-11gR2-preinstall.x86_64 
已加载插件：fastestmirror
Loading mirror speeds from cached hostfile
正在解决依赖关系
--> 正在检查事务
---> 软件包 oracle-rdbms-server-11gR2-preinstall.x86_64.0.1.0-6.el7 将被 安装
--> 正在处理依赖关系 xorg-x11-utils，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 bind-utils，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 gcc-c++，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 kernel-uek，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 compat-libcap1，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 ksh，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 libaio-devel，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 xorg-x11-xauth，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 compat-libstdc++-33，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 libstdc++-devel，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 nfs-utils，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在处理依赖关系 smartmontools，它被软件包 oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64 需要
--> 正在检查事务
---> 软件包 bind-utils.x86_64.32.9.11.4-9.P2.el7 将被 安装
--> 正在处理依赖关系 bind-libs-lite(x86-64) = 32:9.11.4-9.P2.el7，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 bind-libs(x86-64) = 32:9.11.4-9.P2.el7，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 liblwres.so.160()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 libisccfg.so.160()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 libisc.so.169()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 libirs.so.160()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 libdns.so.1102()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
--> 正在处理依赖关系 libbind9.so.160()(64bit)，它被软件包 32:bind-utils-9.11.4-9.P2.el7.x86_64 需要
---> 软件包 compat-libcap1.x86_64.0.1.10-7.el7 将被 安装
---> 软件包 compat-libstdc++-33.x86_64.0.3.2.3-72.el7 将被 安装
---> 软件包 gcc-c++.x86_64.0.4.8.5-39.0.3.el7 将被 安装
--> 正在处理依赖关系 gcc = 4.8.5-39.0.3.el7，它被软件包 gcc-c++-4.8.5-39.0.3.el7.x86_64 需要
--> 正在处理依赖关系 libstdc++ = 4.8.5-39.0.3.el7，它被软件包 gcc-c++-4.8.5-39.0.3.el7.x86_64 需要
---> 软件包 kernel-container.x86_64.0.3.10.0-0.0.0.2.el7 将被 安装
---> 软件包 ksh.x86_64.0.20120801-139.0.1.el7 将被 安装
---> 软件包 libaio-devel.x86_64.0.0.3.109-13.el7 将被 安装
---> 软件包 libstdc++-devel.x86_64.0.4.8.5-39.0.3.el7 将被 安装
---> 软件包 nfs-utils.x86_64.1.1.3.0-0.65.0.1.el7 将被 安装
--> 正在处理依赖关系 gssproxy >= 0.7.0-3，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libtirpc >= 0.2.4-0.7，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 rpcbind，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 keyutils，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libevent，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libnfsidmap，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 quota，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libevent-2.0.so.5()(64bit)，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libtirpc.so.1()(64bit)，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libnfsidmap.so.0()(64bit)，它被软件包 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64 需要
---> 软件包 smartmontools.x86_64.1.7.0-1.el7_7.1 将被 安装
---> 软件包 xorg-x11-utils.x86_64.0.7.5-23.el7 将被 安装
--> 正在处理依赖关系 libxcb.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libxcb-shape.so.0()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libdmx.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXxf86vm.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXxf86misc.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXxf86dga.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXv.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXtst.so.6()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXrender.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXrandr.so.2()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXinerama.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXi.so.6()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libXext.so.6()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libX11.so.6()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
--> 正在处理依赖关系 libX11-xcb.so.1()(64bit)，它被软件包 xorg-x11-utils-7.5-23.el7.x86_64 需要
---> 软件包 xorg-x11-xauth.x86_64.1.1.0.9-1.el7 将被 安装
--> 正在处理依赖关系 libXmuu.so.1()(64bit)，它被软件包 1:xorg-x11-xauth-1.0.9-1.el7.x86_64 需要
--> 正在处理依赖关系 libXau.so.6()(64bit)，它被软件包 1:xorg-x11-xauth-1.0.9-1.el7.x86_64 需要
--> 正在检查事务
---> 软件包 bind-libs.x86_64.32.9.11.4-9.P2.el7 将被 安装
--> 正在处理依赖关系 bind-license = 32:9.11.4-9.P2.el7，它被软件包 32:bind-libs-9.11.4-9.P2.el7.x86_64 需要
---> 软件包 bind-libs-lite.x86_64.32.9.9.4-74.el7_6.1 将被 升级
--> 正在处理依赖关系 libdns-export.so.100()(64bit)，它被软件包 12:dhclient-4.2.5-68.el7.centos.1.x86_64 需要
--> 正在处理依赖关系 libisc-export.so.95()(64bit)，它被软件包 12:dhclient-4.2.5-68.el7.centos.1.x86_64 需要
---> 软件包 bind-libs-lite.x86_64.32.9.11.4-9.P2.el7 将被 更新
---> 软件包 gcc.x86_64.0.4.8.5-36.el7_6.2 将被 升级
---> 软件包 gcc.x86_64.0.4.8.5-39.0.3.el7 将被 更新
--> 正在处理依赖关系 libgomp = 4.8.5-39.0.3.el7，它被软件包 gcc-4.8.5-39.0.3.el7.x86_64 需要
--> 正在处理依赖关系 cpp = 4.8.5-39.0.3.el7，它被软件包 gcc-4.8.5-39.0.3.el7.x86_64 需要
--> 正在处理依赖关系 libgcc >= 4.8.5-39.0.3.el7，它被软件包 gcc-4.8.5-39.0.3.el7.x86_64 需要
---> 软件包 gssproxy.x86_64.0.0.7.0-26.el7 将被 安装
--> 正在处理依赖关系 libini_config >= 1.3.1-31，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libverto-module-base，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libref_array.so.1(REF_ARRAY_0.1.1)(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libini_config.so.3(INI_CONFIG_1.2.0)(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libini_config.so.3(INI_CONFIG_1.1.0)(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libref_array.so.1()(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libini_config.so.3()(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libcollection.so.2()(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
--> 正在处理依赖关系 libbasicobjects.so.0()(64bit)，它被软件包 gssproxy-0.7.0-26.el7.x86_64 需要
---> 软件包 keyutils.x86_64.0.1.5.8-3.el7 将被 安装
---> 软件包 libX11.x86_64.0.1.6.7-2.el7 将被 安装
--> 正在处理依赖关系 libX11-common >= 1.6.7-2.el7，它被软件包 libX11-1.6.7-2.el7.x86_64 需要
---> 软件包 libXau.x86_64.0.1.0.8-2.1.el7 将被 安装
---> 软件包 libXext.x86_64.0.1.3.3-3.el7 将被 安装
---> 软件包 libXi.x86_64.0.1.7.9-1.el7 将被 安装
---> 软件包 libXinerama.x86_64.0.1.1.3-2.1.el7 将被 安装
---> 软件包 libXmu.x86_64.0.1.1.2-2.el7 将被 安装
--> 正在处理依赖关系 libXt.so.6()(64bit)，它被软件包 libXmu-1.1.2-2.el7.x86_64 需要
---> 软件包 libXrandr.x86_64.0.1.5.1-2.el7 将被 安装
---> 软件包 libXrender.x86_64.0.0.9.10-1.el7 将被 安装
---> 软件包 libXtst.x86_64.0.1.2.3-1.el7 将被 安装
---> 软件包 libXv.x86_64.0.1.0.11-1.el7 将被 安装
---> 软件包 libXxf86dga.x86_64.0.1.1.4-2.1.el7 将被 安装
---> 软件包 libXxf86misc.x86_64.0.1.0.3-7.1.el7 将被 安装
---> 软件包 libXxf86vm.x86_64.0.1.1.4-1.el7 将被 安装
---> 软件包 libdmx.x86_64.0.1.1.3-3.el7 将被 安装
---> 软件包 libevent.x86_64.0.2.0.21-4.el7 将被 安装
---> 软件包 libnfsidmap.x86_64.0.0.25-19.el7 将被 安装
---> 软件包 libstdc++.x86_64.0.4.8.5-36.el7_6.2 将被 升级
---> 软件包 libstdc++.x86_64.0.4.8.5-39.0.3.el7 将被 更新
---> 软件包 libtirpc.x86_64.0.0.2.4-0.16.el7 将被 安装
---> 软件包 libxcb.x86_64.0.1.13-1.el7 将被 安装
---> 软件包 quota.x86_64.1.4.01-19.el7 将被 安装
--> 正在处理依赖关系 quota-nls = 1:4.01-19.el7，它被软件包 1:quota-4.01-19.el7.x86_64 需要
--> 正在处理依赖关系 tcp_wrappers，它被软件包 1:quota-4.01-19.el7.x86_64 需要
---> 软件包 rpcbind.x86_64.0.0.2.0-48.el7 将被 安装
--> 正在检查事务
---> 软件包 bind-license.noarch.32.9.9.4-74.el7_6.1 将被 升级
---> 软件包 bind-license.noarch.32.9.11.4-9.P2.el7 将被 更新
---> 软件包 cpp.x86_64.0.4.8.5-36.el7_6.2 将被 升级
---> 软件包 cpp.x86_64.0.4.8.5-39.0.3.el7 将被 更新
---> 软件包 dhclient.x86_64.12.4.2.5-68.el7.centos.1 将被 升级
---> 软件包 dhclient.x86_64.12.4.2.5-77.0.1.el7 将被 更新
--> 正在处理依赖关系 dhcp-common = 12:4.2.5-77.0.1.el7，它被软件包 12:dhclient-4.2.5-77.0.1.el7.x86_64 需要
--> 正在处理依赖关系 dhcp-libs(x86-64) = 12:4.2.5-77.0.1.el7，它被软件包 12:dhclient-4.2.5-77.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libdns-export.so.1102()(64bit)，它被软件包 12:dhclient-4.2.5-77.0.1.el7.x86_64 需要
--> 正在处理依赖关系 libisc-export.so.169()(64bit)，它被软件包 12:dhclient-4.2.5-77.0.1.el7.x86_64 需要
---> 软件包 libX11-common.noarch.0.1.6.7-2.el7 将被 安装
---> 软件包 libXt.x86_64.0.1.1.5-3.el7 将被 安装
--> 正在处理依赖关系 libSM.so.6()(64bit)，它被软件包 libXt-1.1.5-3.el7.x86_64 需要
--> 正在处理依赖关系 libICE.so.6()(64bit)，它被软件包 libXt-1.1.5-3.el7.x86_64 需要
---> 软件包 libbasicobjects.x86_64.0.0.1.1-32.el7 将被 安装
---> 软件包 libcollection.x86_64.0.0.7.0-32.el7 将被 安装
---> 软件包 libgcc.x86_64.0.4.8.5-36.el7_6.2 将被 升级
---> 软件包 libgcc.x86_64.0.4.8.5-39.0.3.el7 将被 更新
---> 软件包 libgomp.x86_64.0.4.8.5-36.el7_6.2 将被 升级
---> 软件包 libgomp.x86_64.0.4.8.5-39.0.3.el7 将被 更新
---> 软件包 libini_config.x86_64.0.1.3.1-32.el7 将被 安装
--> 正在处理依赖关系 libpath_utils.so.1(PATH_UTILS_0.2.1)(64bit)，它被软件包 libini_config-1.3.1-32.el7.x86_64 需要
--> 正在处理依赖关系 libpath_utils.so.1()(64bit)，它被软件包 libini_config-1.3.1-32.el7.x86_64 需要
---> 软件包 libref_array.x86_64.0.0.1.5-32.el7 将被 安装
---> 软件包 libverto-libevent.x86_64.0.0.2.5-4.el7 将被 安装
---> 软件包 quota-nls.noarch.1.4.01-19.el7 将被 安装
---> 软件包 tcp_wrappers.x86_64.0.7.6-77.el7 将被 安装
--> 正在检查事务
---> 软件包 bind-export-libs.x86_64.32.9.11.4-9.P2.el7 将被 安装
---> 软件包 dhcp-common.x86_64.12.4.2.5-68.el7.centos.1 将被 升级
---> 软件包 dhcp-common.x86_64.12.4.2.5-77.0.1.el7 将被 更新
---> 软件包 dhcp-libs.x86_64.12.4.2.5-68.el7.centos.1 将被 升级
---> 软件包 dhcp-libs.x86_64.12.4.2.5-77.0.1.el7 将被 更新
---> 软件包 libICE.x86_64.0.1.0.9-9.el7 将被 安装
---> 软件包 libSM.x86_64.0.1.2.2-2.el7 将被 安装
---> 软件包 libpath_utils.x86_64.0.0.2.1-32.el7 将被 安装
--> 解决依赖关系完成

依赖关系解决

===================================================================================================
 Package                                  架构       版本                     源              大小
===================================================================================================
正在安装:
 oracle-rdbms-server-11gR2-preinstall     x86_64     1.0-6.el7                ol7_latest      22 k
为依赖而安装:
 bind-export-libs                         x86_64     32:9.11.4-9.P2.el7       base           1.1 M
 bind-libs                                x86_64     32:9.11.4-9.P2.el7       base           154 k
 bind-utils                               x86_64     32:9.11.4-9.P2.el7       base           258 k
 compat-libcap1                           x86_64     1.10-7.el7               base            19 k
 compat-libstdc++-33                      x86_64     3.2.3-72.el7             base           191 k
 gcc-c++                                  x86_64     4.8.5-39.0.3.el7         ol7_latest     7.2 M
 gssproxy                                 x86_64     0.7.0-26.el7             base           110 k
 kernel-container                         x86_64     3.10.0-0.0.0.2.el7       ol7_latest     2.6 k
 keyutils                                 x86_64     1.5.8-3.el7              base            54 k
 ksh                                      x86_64     20120801-139.0.1.el7     ol7_latest     883 k
 libICE                                   x86_64     1.0.9-9.el7              base            66 k
 libSM                                    x86_64     1.2.2-2.el7              base            39 k
 libX11                                   x86_64     1.6.7-2.el7              base           607 k
 libX11-common                            noarch     1.6.7-2.el7              base           164 k
 libXau                                   x86_64     1.0.8-2.1.el7            base            29 k
 libXext                                  x86_64     1.3.3-3.el7              base            39 k
 libXi                                    x86_64     1.7.9-1.el7              base            40 k
 libXinerama                              x86_64     1.1.3-2.1.el7            base            14 k
 libXmu                                   x86_64     1.1.2-2.el7              base            71 k
 libXrandr                                x86_64     1.5.1-2.el7              base            27 k
 libXrender                               x86_64     0.9.10-1.el7             base            26 k
 libXt                                    x86_64     1.1.5-3.el7              base           173 k
 libXtst                                  x86_64     1.2.3-1.el7              base            20 k
 libXv                                    x86_64     1.0.11-1.el7             base            18 k
 libXxf86dga                              x86_64     1.1.4-2.1.el7            base            19 k
 libXxf86misc                             x86_64     1.0.3-7.1.el7            base            19 k
 libXxf86vm                               x86_64     1.1.4-1.el7              base            18 k
 libaio-devel                             x86_64     0.3.109-13.el7           base            13 k
 libbasicobjects                          x86_64     0.1.1-32.el7             base            26 k
 libcollection                            x86_64     0.7.0-32.el7             base            42 k
 libdmx                                   x86_64     1.1.3-3.el7              base            16 k
 libevent                                 x86_64     2.0.21-4.el7             base           214 k
 libini_config                            x86_64     1.3.1-32.el7             base            64 k
 libnfsidmap                              x86_64     0.25-19.el7              base            50 k
 libpath_utils                            x86_64     0.2.1-32.el7             base            28 k
 libref_array                             x86_64     0.1.5-32.el7             base            27 k
 libstdc++-devel                          x86_64     4.8.5-39.0.3.el7         ol7_latest     1.5 M
 libtirpc                                 x86_64     0.2.4-0.16.el7           base            89 k
 libverto-libevent                        x86_64     0.2.5-4.el7              base           8.9 k
 libxcb                                   x86_64     1.13-1.el7               base           214 k
 nfs-utils                                x86_64     1:1.3.0-0.65.0.1.el7     ol7_latest     412 k
 quota                                    x86_64     1:4.01-19.el7            base           179 k
 quota-nls                                noarch     1:4.01-19.el7            base            90 k
 rpcbind                                  x86_64     0.2.0-48.el7             base            60 k
 smartmontools                            x86_64     1:7.0-1.el7_7.1          ol7_latest     546 k
 tcp_wrappers                             x86_64     7.6-77.el7               base            78 k
 xorg-x11-utils                           x86_64     7.5-23.el7               base           114 k
 xorg-x11-xauth                           x86_64     1:1.0.9-1.el7            base            30 k
为依赖而更新:
 bind-libs-lite                           x86_64     32:9.11.4-9.P2.el7       base           1.1 M
 bind-license                             noarch     32:9.11.4-9.P2.el7       base            88 k
 cpp                                      x86_64     4.8.5-39.0.3.el7         ol7_latest     6.0 M
 dhclient                                 x86_64     12:4.2.5-77.0.1.el7      ol7_latest     285 k
 dhcp-common                              x86_64     12:4.2.5-77.0.1.el7      ol7_latest     175 k
 dhcp-libs                                x86_64     12:4.2.5-77.0.1.el7      ol7_latest     132 k
 gcc                                      x86_64     4.8.5-39.0.3.el7         ol7_latest      16 M
 libgcc                                   x86_64     4.8.5-39.0.3.el7         ol7_latest     103 k
 libgomp                                  x86_64     4.8.5-39.0.3.el7         ol7_latest     158 k
 libstdc++                                x86_64     4.8.5-39.0.3.el7         ol7_latest     306 k

事务概要
===================================================================================================
安装  1 软件包 (+48 依赖软件包)
升级           ( 10 依赖软件包)

总下载量：40 M
Is this ok [y/d/N]: y
Downloading packages:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
(1/59): bind-libs-9.11.4-9.P2.el7.x86_64.rpm                                | 154 kB  00:00:00     
(2/59): bind-libs-lite-9.11.4-9.P2.el7.x86_64.rpm                           | 1.1 MB  00:00:00     
(3/59): bind-export-libs-9.11.4-9.P2.el7.x86_64.rpm                         | 1.1 MB  00:00:00     
(4/59): bind-license-9.11.4-9.P2.el7.noarch.rpm                             |  88 kB  00:00:00     
(5/59): bind-utils-9.11.4-9.P2.el7.x86_64.rpm                               | 258 kB  00:00:00     
(6/59): compat-libstdc++-33-3.2.3-72.el7.x86_64.rpm                         | 191 kB  00:00:00     
(7/59): compat-libcap1-1.10-7.el7.x86_64.rpm                                |  19 kB  00:00:00     
warning: /var/cache/yum/x86_64/7/ol7_latest/packages/dhclient-4.2.5-77.0.1.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID ec551f03: NOKEY
dhclient-4.2.5-77.0.1.el7.x86_64.rpm 的公钥尚未安装
(8/59): dhclient-4.2.5-77.0.1.el7.x86_64.rpm                                | 285 kB  00:00:05     
(9/59): dhcp-common-4.2.5-77.0.1.el7.x86_64.rpm                             | 175 kB  00:00:00     
(10/59): dhcp-libs-4.2.5-77.0.1.el7.x86_64.rpm                              | 132 kB  00:00:00     
(11/59): cpp-4.8.5-39.0.3.el7.x86_64.rpm                                    | 6.0 MB  00:00:08     
(12/59): gssproxy-0.7.0-26.el7.x86_64.rpm                                   | 110 kB  00:00:00     
(13/59): gcc-4.8.5-39.0.3.el7.x86_64.rpm                                    |  16 MB  00:00:04     
(14/59): keyutils-1.5.8-3.el7.x86_64.rpm                                    |  54 kB  00:00:00     
(15/59): kernel-container-3.10.0-0.0.0.2.el7.x86_64.rpm                     | 2.6 kB  00:00:00     
(16/59): libICE-1.0.9-9.el7.x86_64.rpm                                      |  66 kB  00:00:00     
(17/59): libSM-1.2.2-2.el7.x86_64.rpm                                       |  39 kB  00:00:00     
(18/59): libX11-common-1.6.7-2.el7.noarch.rpm                               | 164 kB  00:00:00     
(19/59): libXau-1.0.8-2.1.el7.x86_64.rpm                                    |  29 kB  00:00:00     
(20/59): libXext-1.3.3-3.el7.x86_64.rpm                                     |  39 kB  00:00:00     
(21/59): libXi-1.7.9-1.el7.x86_64.rpm                                       |  40 kB  00:00:00     
(22/59): libX11-1.6.7-2.el7.x86_64.rpm                                      | 607 kB  00:00:00     
(23/59): libXinerama-1.1.3-2.1.el7.x86_64.rpm                               |  14 kB  00:00:00     
(24/59): libXrandr-1.5.1-2.el7.x86_64.rpm                                   |  27 kB  00:00:00     
(25/59): libXrender-0.9.10-1.el7.x86_64.rpm                                 |  26 kB  00:00:00     
(26/59): libXt-1.1.5-3.el7.x86_64.rpm                                       | 173 kB  00:00:00     
(27/59): libXtst-1.2.3-1.el7.x86_64.rpm                                     |  20 kB  00:00:00     
(28/59): libXmu-1.1.2-2.el7.x86_64.rpm                                      |  71 kB  00:00:00     
(29/59): libXv-1.0.11-1.el7.x86_64.rpm                                      |  18 kB  00:00:00     
(30/59): libXxf86misc-1.0.3-7.1.el7.x86_64.rpm                              |  19 kB  00:00:00     
(31/59): libXxf86vm-1.1.4-1.el7.x86_64.rpm                                  |  18 kB  00:00:00     
(32/59): libXxf86dga-1.1.4-2.1.el7.x86_64.rpm                               |  19 kB  00:00:00     
(33/59): libaio-devel-0.3.109-13.el7.x86_64.rpm                             |  13 kB  00:00:00     
(34/59): libbasicobjects-0.1.1-32.el7.x86_64.rpm                            |  26 kB  00:00:00     
(35/59): libcollection-0.7.0-32.el7.x86_64.rpm                              |  42 kB  00:00:00     
(36/59): libdmx-1.1.3-3.el7.x86_64.rpm                                      |  16 kB  00:00:00     
(37/59): gcc-c++-4.8.5-39.0.3.el7.x86_64.rpm                                | 7.2 MB  00:00:03     
(38/59): libevent-2.0.21-4.el7.x86_64.rpm                                   | 214 kB  00:00:00     
(39/59): ksh-20120801-139.0.1.el7.x86_64.rpm                                | 883 kB  00:00:00     
(40/59): libini_config-1.3.1-32.el7.x86_64.rpm                              |  64 kB  00:00:00     
(41/59): libgcc-4.8.5-39.0.3.el7.x86_64.rpm                                 | 103 kB  00:00:00     
(42/59): libpath_utils-0.2.1-32.el7.x86_64.rpm                              |  28 kB  00:00:00     
(43/59): libref_array-0.1.5-32.el7.x86_64.rpm                               |  27 kB  00:00:00     
(44/59): libnfsidmap-0.25-19.el7.x86_64.rpm                                 |  50 kB  00:00:00     
(45/59): libgomp-4.8.5-39.0.3.el7.x86_64.rpm                                | 158 kB  00:00:00     
(46/59): libtirpc-0.2.4-0.16.el7.x86_64.rpm                                 |  89 kB  00:00:00     
(47/59): libxcb-1.13-1.el7.x86_64.rpm                                       | 214 kB  00:00:00     
(48/59): libstdc++-4.8.5-39.0.3.el7.x86_64.rpm                              | 306 kB  00:00:00     
(49/59): libverto-libevent-0.2.5-4.el7.x86_64.rpm                           | 8.9 kB  00:00:00     
(50/59): nfs-utils-1.3.0-0.65.0.1.el7.x86_64.rpm                            | 412 kB  00:00:00     
(51/59): quota-4.01-19.el7.x86_64.rpm                                       | 179 kB  00:00:00     
(52/59): rpcbind-0.2.0-48.el7.x86_64.rpm                                    |  60 kB  00:00:00     
(53/59): quota-nls-4.01-19.el7.noarch.rpm                                   |  90 kB  00:00:00     
(54/59): oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64.rpm          |  22 kB  00:00:00     
(55/59): tcp_wrappers-7.6-77.el7.x86_64.rpm                                 |  78 kB  00:00:00     
(56/59): xorg-x11-xauth-1.0.9-1.el7.x86_64.rpm                              |  30 kB  00:00:00     
(57/59): xorg-x11-utils-7.5-23.el7.x86_64.rpm                               | 114 kB  00:00:00     
(58/59): libstdc++-devel-4.8.5-39.0.3.el7.x86_64.rpm                        | 1.5 MB  00:00:00     
(59/59): smartmontools-7.0-1.el7_7.1.x86_64.rpm                             | 546 kB  00:00:00     
---------------------------------------------------------------------------------------------------
总计                                                               3.0 MB/s |  40 MB  00:00:13     
从 file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle 检索密钥
导入 GPG key 0xEC551F03:
 用户ID     : "Oracle OSS group (Open Source Software group) <build@oss.oracle.com>"
 指纹       : 4214 4123 fecf c55b 9086 313d 72f9 7b74 ec55 1f03
 来自       : /etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
是否继续？[y/N]：y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  正在更新    : libgcc-4.8.5-39.0.3.el7.x86_64                                                1/69 
  正在更新    : libstdc++-4.8.5-39.0.3.el7.x86_64                                             2/69 
  正在安装    : libstdc++-devel-4.8.5-39.0.3.el7.x86_64                                       3/69 
  正在安装    : libXau-1.0.8-2.1.el7.x86_64                                                   4/69 
  正在安装    : libxcb-1.13-1.el7.x86_64                                                      5/69 
  正在安装    : libcollection-0.7.0-32.el7.x86_64                                             6/69 
  正在安装    : libICE-1.0.9-9.el7.x86_64                                                     7/69 
  正在安装    : libref_array-0.1.5-32.el7.x86_64                                              8/69 
  正在安装    : libevent-2.0.21-4.el7.x86_64                                                  9/69 
  正在更新    : 32:bind-license-9.11.4-9.P2.el7.noarch                                       10/69 
  正在更新    : 32:bind-libs-lite-9.11.4-9.P2.el7.x86_64                                     11/69 
  正在更新    : 12:dhcp-libs-4.2.5-77.0.1.el7.x86_64                                         12/69 
  正在安装    : libbasicobjects-0.1.1-32.el7.x86_64                                          13/69 
  正在安装    : libtirpc-0.2.4-0.16.el7.x86_64                                               14/69 
  正在安装    : rpcbind-0.2.0-48.el7.x86_64                                                  15/69 
  正在更新    : 12:dhcp-common-4.2.5-77.0.1.el7.x86_64                                       16/69 
  正在安装    : 32:bind-libs-9.11.4-9.P2.el7.x86_64                                          17/69 
  正在安装    : 32:bind-utils-9.11.4-9.P2.el7.x86_64                                         18/69 
  正在安装    : libverto-libevent-0.2.5-4.el7.x86_64                                         19/69 
  正在安装    : libSM-1.2.2-2.el7.x86_64                                                     20/69 
  正在安装    : 1:smartmontools-7.0-1.el7_7.1.x86_64                                         21/69 
  正在安装    : compat-libstdc++-33-3.2.3-72.el7.x86_64                                      22/69 
  正在安装    : 1:quota-nls-4.01-19.el7.noarch                                               23/69 
  正在更新    : cpp-4.8.5-39.0.3.el7.x86_64                                                  24/69 
  正在安装    : keyutils-1.5.8-3.el7.x86_64                                                  25/69 
  正在安装    : libnfsidmap-0.25-19.el7.x86_64                                               26/69 
  正在安装    : ksh-20120801-139.0.1.el7.x86_64                                              27/69 
  正在安装    : libaio-devel-0.3.109-13.el7.x86_64                                           28/69 
  正在安装    : compat-libcap1-1.10-7.el7.x86_64                                             29/69 
  正在安装    : 32:bind-export-libs-9.11.4-9.P2.el7.x86_64                                   30/69 
  正在更新    : libgomp-4.8.5-39.0.3.el7.x86_64                                              31/69 
  正在更新    : gcc-4.8.5-39.0.3.el7.x86_64                                                  32/69 
  正在安装    : gcc-c++-4.8.5-39.0.3.el7.x86_64                                              33/69 
  正在安装    : libX11-common-1.6.7-2.el7.noarch                                             34/69 
  正在安装    : libX11-1.6.7-2.el7.x86_64                                                    35/69 
  正在安装    : libXext-1.3.3-3.el7.x86_64                                                   36/69 
  正在安装    : libXi-1.7.9-1.el7.x86_64                                                     37/69 
  正在安装    : libXrender-0.9.10-1.el7.x86_64                                               38/69 
  正在安装    : libXrandr-1.5.1-2.el7.x86_64                                                 39/69 
  正在安装    : libXtst-1.2.3-1.el7.x86_64                                                   40/69 
  正在安装    : libXxf86misc-1.0.3-7.1.el7.x86_64                                            41/69 
  正在安装    : libdmx-1.1.3-3.el7.x86_64                                                    42/69 
  正在安装    : libXinerama-1.1.3-2.1.el7.x86_64                                             43/69 
  正在安装    : libXv-1.0.11-1.el7.x86_64                                                    44/69 
  正在安装    : libXxf86vm-1.1.4-1.el7.x86_64                                                45/69 
  正在安装    : libXxf86dga-1.1.4-2.1.el7.x86_64                                             46/69 
  正在安装    : xorg-x11-utils-7.5-23.el7.x86_64                                             47/69 
  正在安装    : libXt-1.1.5-3.el7.x86_64                                                     48/69 
  正在安装    : libXmu-1.1.2-2.el7.x86_64                                                    49/69 
  正在安装    : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                          50/69 
  正在安装    : tcp_wrappers-7.6-77.el7.x86_64                                               51/69 
  正在安装    : 1:quota-4.01-19.el7.x86_64                                                   52/69 
  正在安装    : libpath_utils-0.2.1-32.el7.x86_64                                            53/69 
  正在安装    : libini_config-1.3.1-32.el7.x86_64                                            54/69 
  正在安装    : gssproxy-0.7.0-26.el7.x86_64                                                 55/69 
  正在安装    : 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64                                        56/69 
  正在安装    : kernel-container-3.10.0-0.0.0.2.el7.x86_64                                   57/69 
  正在安装    : oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64                        58/69 
  正在更新    : 12:dhclient-4.2.5-77.0.1.el7.x86_64                                          59/69 
  清理        : 12:dhclient-4.2.5-68.el7.centos.1.x86_64                                     60/69 
  清理        : gcc-4.8.5-36.el7_6.2.x86_64                                                  61/69 
  清理        : 12:dhcp-common-4.2.5-68.el7.centos.1.x86_64                                  62/69 
  清理        : 32:bind-libs-lite-9.9.4-74.el7_6.1.x86_64                                    63/69 
  清理        : libstdc++-4.8.5-36.el7_6.2.x86_64                                            64/69 
  清理        : 32:bind-license-9.9.4-74.el7_6.1.noarch                                      65/69 
  清理        : 12:dhcp-libs-4.2.5-68.el7.centos.1.x86_64                                    66/69 
  清理        : libgcc-4.8.5-36.el7_6.2.x86_64                                               67/69 
  清理        : cpp-4.8.5-36.el7_6.2.x86_64                                                  68/69 
  清理        : libgomp-4.8.5-36.el7_6.2.x86_64                                              69/69 
  验证中      : libtirpc-0.2.4-0.16.el7.x86_64                                                1/69 
  验证中      : libXext-1.3.3-3.el7.x86_64                                                    2/69 
  验证中      : libXxf86misc-1.0.3-7.1.el7.x86_64                                             3/69 
  验证中      : libdmx-1.1.3-3.el7.x86_64                                                     4/69 
  验证中      : oracle-rdbms-server-11gR2-preinstall-1.0-6.el7.x86_64                         5/69 
  验证中      : libXinerama-1.1.3-2.1.el7.x86_64                                              6/69 
  验证中      : libXrender-0.9.10-1.el7.x86_64                                                7/69 
  验证中      : libXt-1.1.5-3.el7.x86_64                                                      8/69 
  验证中      : libXv-1.0.11-1.el7.x86_64                                                     9/69 
  验证中      : libXi-1.7.9-1.el7.x86_64                                                     10/69 
  验证中      : libXxf86vm-1.1.4-1.el7.x86_64                                                11/69 
  验证中      : kernel-container-3.10.0-0.0.0.2.el7.x86_64                                   12/69 
  验证中      : libbasicobjects-0.1.1-32.el7.x86_64                                          13/69 
  验证中      : 32:bind-utils-9.11.4-9.P2.el7.x86_64                                         14/69 
  验证中      : libgcc-4.8.5-39.0.3.el7.x86_64                                               15/69 
  验证中      : libpath_utils-0.2.1-32.el7.x86_64                                            16/69 
  验证中      : tcp_wrappers-7.6-77.el7.x86_64                                               17/69 
  验证中      : 12:dhcp-common-4.2.5-77.0.1.el7.x86_64                                       18/69 
  验证中      : libstdc++-4.8.5-39.0.3.el7.x86_64                                            19/69 
  验证中      : libstdc++-devel-4.8.5-39.0.3.el7.x86_64                                      20/69 
  验证中      : xorg-x11-utils-7.5-23.el7.x86_64                                             21/69 
  验证中      : 1:nfs-utils-1.3.0-0.65.0.1.el7.x86_64                                        22/69 
  验证中      : libXtst-1.2.3-1.el7.x86_64                                                   23/69 
  验证中      : libX11-1.6.7-2.el7.x86_64                                                    24/69 
  验证中      : libX11-common-1.6.7-2.el7.noarch                                             25/69 
  验证中      : libxcb-1.13-1.el7.x86_64                                                     26/69 
  验证中      : libgomp-4.8.5-39.0.3.el7.x86_64                                              27/69 
  验证中      : 12:dhcp-libs-4.2.5-77.0.1.el7.x86_64                                         28/69 
  验证中      : libini_config-1.3.1-32.el7.x86_64                                            29/69 
  验证中      : 32:bind-export-libs-9.11.4-9.P2.el7.x86_64                                   30/69 
  验证中      : gcc-c++-4.8.5-39.0.3.el7.x86_64                                              31/69 
  验证中      : 32:bind-license-9.11.4-9.P2.el7.noarch                                       32/69 
  验证中      : libevent-2.0.21-4.el7.x86_64                                                 33/69 
  验证中      : libverto-libevent-0.2.5-4.el7.x86_64                                         34/69 
  验证中      : compat-libcap1-1.10-7.el7.x86_64                                             35/69 
  验证中      : libXrandr-1.5.1-2.el7.x86_64                                                 36/69 
  验证中      : libaio-devel-0.3.109-13.el7.x86_64                                           37/69 
  验证中      : 12:dhclient-4.2.5-77.0.1.el7.x86_64                                          38/69 
  验证中      : libref_array-0.1.5-32.el7.x86_64                                             39/69 
  验证中      : 32:bind-libs-lite-9.11.4-9.P2.el7.x86_64                                     40/69 
  验证中      : 1:smartmontools-7.0-1.el7_7.1.x86_64                                         41/69 
  验证中      : rpcbind-0.2.0-48.el7.x86_64                                                  42/69 
  验证中      : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                          43/69 
  验证中      : libICE-1.0.9-9.el7.x86_64                                                    44/69 
  验证中      : ksh-20120801-139.0.1.el7.x86_64                                              45/69 
  验证中      : 1:quota-4.01-19.el7.x86_64                                                   46/69 
  验证中      : gssproxy-0.7.0-26.el7.x86_64                                                 47/69 
  验证中      : libnfsidmap-0.25-19.el7.x86_64                                               48/69 
  验证中      : libSM-1.2.2-2.el7.x86_64                                                     49/69 
  验证中      : libXxf86dga-1.1.4-2.1.el7.x86_64                                             50/69 
  验证中      : libXmu-1.1.2-2.el7.x86_64                                                    51/69 
  验证中      : keyutils-1.5.8-3.el7.x86_64                                                  52/69 
  验证中      : compat-libstdc++-33-3.2.3-72.el7.x86_64                                      53/69 
  验证中      : libcollection-0.7.0-32.el7.x86_64                                            54/69 
  验证中      : libXau-1.0.8-2.1.el7.x86_64                                                  55/69 
  验证中      : cpp-4.8.5-39.0.3.el7.x86_64                                                  56/69 
  验证中      : 1:quota-nls-4.01-19.el7.noarch                                               57/69 
  验证中      : 32:bind-libs-9.11.4-9.P2.el7.x86_64                                          58/69 
  验证中      : gcc-4.8.5-39.0.3.el7.x86_64                                                  59/69 
  验证中      : gcc-4.8.5-36.el7_6.2.x86_64                                                  60/69 
  验证中      : 32:bind-license-9.9.4-74.el7_6.1.noarch                                      61/69 
  验证中      : 12:dhclient-4.2.5-68.el7.centos.1.x86_64                                     62/69 
  验证中      : libstdc++-4.8.5-36.el7_6.2.x86_64                                            63/69 
  验证中      : libgomp-4.8.5-36.el7_6.2.x86_64                                              64/69 
  验证中      : 12:dhcp-libs-4.2.5-68.el7.centos.1.x86_64                                    65/69 
  验证中      : 12:dhcp-common-4.2.5-68.el7.centos.1.x86_64                                  66/69 
  验证中      : libgcc-4.8.5-36.el7_6.2.x86_64                                               67/69 
  验证中      : cpp-4.8.5-36.el7_6.2.x86_64                                                  68/69 
  验证中      : 32:bind-libs-lite-9.9.4-74.el7_6.1.x86_64                                    69/69 

已安装:
  oracle-rdbms-server-11gR2-preinstall.x86_64 0:1.0-6.el7                                          

作为依赖被安装:
  bind-export-libs.x86_64 32:9.11.4-9.P2.el7      bind-libs.x86_64 32:9.11.4-9.P2.el7              
  bind-utils.x86_64 32:9.11.4-9.P2.el7            compat-libcap1.x86_64 0:1.10-7.el7               
  compat-libstdc++-33.x86_64 0:3.2.3-72.el7       gcc-c++.x86_64 0:4.8.5-39.0.3.el7                
  gssproxy.x86_64 0:0.7.0-26.el7                  kernel-container.x86_64 0:3.10.0-0.0.0.2.el7     
  keyutils.x86_64 0:1.5.8-3.el7                   ksh.x86_64 0:20120801-139.0.1.el7                
  libICE.x86_64 0:1.0.9-9.el7                     libSM.x86_64 0:1.2.2-2.el7                       
  libX11.x86_64 0:1.6.7-2.el7                     libX11-common.noarch 0:1.6.7-2.el7               
  libXau.x86_64 0:1.0.8-2.1.el7                   libXext.x86_64 0:1.3.3-3.el7                     
  libXi.x86_64 0:1.7.9-1.el7                      libXinerama.x86_64 0:1.1.3-2.1.el7               
  libXmu.x86_64 0:1.1.2-2.el7                     libXrandr.x86_64 0:1.5.1-2.el7                   
  libXrender.x86_64 0:0.9.10-1.el7                libXt.x86_64 0:1.1.5-3.el7                       
  libXtst.x86_64 0:1.2.3-1.el7                    libXv.x86_64 0:1.0.11-1.el7                      
  libXxf86dga.x86_64 0:1.1.4-2.1.el7              libXxf86misc.x86_64 0:1.0.3-7.1.el7              
  libXxf86vm.x86_64 0:1.1.4-1.el7                 libaio-devel.x86_64 0:0.3.109-13.el7             
  libbasicobjects.x86_64 0:0.1.1-32.el7           libcollection.x86_64 0:0.7.0-32.el7              
  libdmx.x86_64 0:1.1.3-3.el7                     libevent.x86_64 0:2.0.21-4.el7                   
  libini_config.x86_64 0:1.3.1-32.el7             libnfsidmap.x86_64 0:0.25-19.el7                 
  libpath_utils.x86_64 0:0.2.1-32.el7             libref_array.x86_64 0:0.1.5-32.el7               
  libstdc++-devel.x86_64 0:4.8.5-39.0.3.el7       libtirpc.x86_64 0:0.2.4-0.16.el7                 
  libverto-libevent.x86_64 0:0.2.5-4.el7          libxcb.x86_64 0:1.13-1.el7                       
  nfs-utils.x86_64 1:1.3.0-0.65.0.1.el7           quota.x86_64 1:4.01-19.el7                       
  quota-nls.noarch 1:4.01-19.el7                  rpcbind.x86_64 0:0.2.0-48.el7                    
  smartmontools.x86_64 1:7.0-1.el7_7.1            tcp_wrappers.x86_64 0:7.6-77.el7                 
  xorg-x11-utils.x86_64 0:7.5-23.el7              xorg-x11-xauth.x86_64 1:1.0.9-1.el7              

作为依赖被升级:
  bind-libs-lite.x86_64 32:9.11.4-9.P2.el7          bind-license.noarch 32:9.11.4-9.P2.el7         
  cpp.x86_64 0:4.8.5-39.0.3.el7                     dhclient.x86_64 12:4.2.5-77.0.1.el7            
  dhcp-common.x86_64 12:4.2.5-77.0.1.el7            dhcp-libs.x86_64 12:4.2.5-77.0.1.el7           
  gcc.x86_64 0:4.8.5-39.0.3.el7                     libgcc.x86_64 0:4.8.5-39.0.3.el7               
  libgomp.x86_64 0:4.8.5-39.0.3.el7                 libstdc++.x86_64 0:4.8.5-39.0.3.el7            

完毕！

```

[Oracle Database Postinstallation Tasks](https://docs.oracle.com/cd/E11882_01/install.112/e47689/post_inst_task.htm#LADBI1260)

解压linux.x64_11gR2_database_1of2.zip 和`linux.x64_11gR2_database_2of2.zip`到相同的目录

复制出`db_install.rsp`

```sh
cp database/response/db_install.rsp ./
chmod 700 db_install.rsp 
```

修改`db_install.rsp`文件

```shell l
./database/runInstaller -silent  -responseFile /home/oracle/db_install.rsp -ignorePrereq
```

没有`Failed`，使用`dbca -h`判断是否安装完成

生成监听文件

```shell
cp database/response/netca.rsp ./

netca /silent -responsefile /home/oracle/netca.rsp 
```

创建数据库

```shell
cp database/response/dbca.rsp ./
 
dbca -silent -responseFile dbca.rsp 

```

登录数据库

```shell
sqlplus / as sysdba
```

创建表空间

```sql
create tablespace mbank datafile '/oracle/oradata/mbank/mbank01.dbf' size 300m autoextend on;
```

创建用户

```sql
create user username identified by password default tablespace user_data temporary tablespace user_temp; 
```

给用户分配权限 `dba`权限imp需要

```sql
grant dba to username;
grant create session,create table,unlimited tablespace to username;
```

修改用户默认表空间

```sql
alert user username default tablespace tablespacename;
```

导入数据

```shell
imp 用户名/密码@SID file=filename.imp log=imp.log ignore=y full=y
```

