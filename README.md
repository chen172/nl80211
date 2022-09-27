for kernel 4.19

# Goal:
analyse when kernel receive generical netlink message, how kernel processing it.

# file description:
1. nl80211.c: interface for wireless generic netlink programming, in /net/wireless dir, is cfg80211 module 
2. nl80211.h: the data structure for nl80211.c, in /net/wireless dir, is cfg80211 module 
3. genetlink.h: genl data structure, in your system /usr/src/linux-head-xxx/include/net dir
4. genetlink.c: genl operation, the interface for nl80211.c, in linux-source/net/netlink dir, is netlink_diag module
5. netlink.h: netlink operation, in your system /usr/src/linux-head-xxx/include/net dir
6. nlattr.c: netlink attribute operation, in linux-source/lib dir

# Ongoing:
1. kernel received message put into genl_info, how kernel put it?
2. use nl80211.c's function process it, for example, nl80211_get_wiphy
3. and then put the processed message into struct sk_buf 


# 编译cfg80211模块
进入内核的源码目录net/wireless

1.修改trace.h文件中的最后的路径为当前目录的路径

2.把Makefile删掉

添加这个Kbuild文件,然后执行下面的命令

```make -C /lib/modules/$(uname -r)/build/ M=$PWD```

# Info:
<img src="picture/Wifi-Sub-Sys.png"></img>

# Data structure
| File | Data structure |
| :---- | :---- |
| net/mac802.11.h | ieee80211_tx_info |

# Ubuntu linux header
/usr/src

# TO DO
how the kernel get struct genl_info
