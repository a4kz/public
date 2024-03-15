出厂默认 emmc 有第三方系统时，需要ssh连接后进入命令行，擦除启动分区

```bash
lsblk #查看一下emmc分区的具体名称
dd if=/dev/zero of=/dev/mmcblk2 bs=8M count=25
```

### 如果 Openwrt 中没有 lsblk 怎么办?

```
df -h 
cat /proc/partitions
fdisk -l
```


### 4.5 eMMC与TF卡的启动优先级说明 (救砖办法)

默认情况下, 会优先从 TF卡启动系统, 但并不是所有条件下都是这样, 本节内容将详细说明所有情况; 

 引用Rockchip官方文档[[1\]](http://opensource.rock-chips.com/wiki_Boot_option)的描述，系统引导程序(Loader)分为以下2种:

1) U-Boot TPL/SPL (即upsream U-Boot, 也叫主线U-Boot)
2) Rockchip MiniLoader


 需要留意的是: 

1) FriendlyELEC发布的所有Rom均采用的都是第2种，即Rockchip MiniLoader
2) 第三方固件通常采用的是第1种,  即  U-Boot TPL/SPL


 以下情况将总是从 eMMC 启动 (意味着无法通过TF卡烧写系统了):

1) 如果eMMC里的系统, 或者TF卡里的系统是采用第一种Loader类型U-Boot TPL/SPL的, 上电将总是从 eMMC启动;
2) eMMC内的系统并没有适配NanoPi-R5C, 也就是说Loader压根就是坏的;


 这时, 可以用如下方法让NanoPi-R5C从TF卡启动系统, 进行系统重装或Flash擦除:

1) 插入一张烧写有FriendlyWrt系统的TF卡 (制作方法请参考上面的章节);
2) 按下Maskrom按键, 并上电开机 (或短接Maskrom触点);
3) **重要**: 上电后默数4秒左右立即松开Maskrom按键;
4) NanoPi-R5C将会从TF卡启动FriendlyWrt系统;
5) 用网线连接电脑到NanoPi-R5C的LAN网口, 在电脑上输入网址 http://192.168.2.1 进入FriendlyWrt管理页面, 使用系统菜单中的eMMC刷机工具重新烧写系统到 eMMC;
6) 如果你仅仅想清除eMMC上的数据, 可以上传一个内容全是零的img文件刷进eMMC, 该文件在电脑上可以用如下命令生成, 因eMMC刷机工具在烧写系统时会先对eMMC进行全面擦除, 所以img文件的大小是不重要的:

```
dd if=/dev/zero of=~/empty.img bs=8M count=1
```

或者, 进入命令终端, 输入以下命令尝试清除eMMC上的 Loader: 

```
dd if=/dev/zero of=/dev/mmcblk2 bs=8M count=25
```



### 常见问题:

 如果用TF卡启动系统后,发现系统检测不到eMMC,可能的原因是上电后按下Markrom键太长时间, 正确方法是按住4秒立即松开; 
 请确认你使用了最新固件(日期2022-07-25之后的固件), 然后重新操作一次;



### 总结如下:

| eMMC当前系统         | TF卡当前系统         | 启动优先级 |
| -------------------- | -------------------- | ---------- |
| 无系统               | 任意固件             | TF卡       |
| FriendlyELEC的固件   | FriendlyELEC的固件   | TF卡       |
| FriendlyELEC的固件   | 采用主线U-boot的固件 | eMMC       |
| 采用主线U-boot的固件 | FriendlyELEC的固件   | eMMC       |
| 采用主线U-boot的固件 | 采用主线U-boot的固件 | eMMC       |

### 完整文档 R5C

https://wiki.friendlyelec.com/wiki/index.php/NanoPi_R5C/zh

-----
### 给Openwrt设置代理
```
cd /etc/profile.d
vi custom.sh
```

```
export https_proxy=http://proxy.example.org:8080/
```

```
. /etc/profile
```
```
# 貌似不必替换也可以
sed -i -e "s/https/http/" /etc/opkg/distfeeds.conf
```

#### 在`/etc/opkg.conf`里写入: 

```
option http_proxy http://proxy.example.org:8080/
option ftp_proxy ftp://proxy.example.org:2121/
```
#### 完整文档
https://openwrt.org/docs/guide-user/additional-software/opkg#proxy_support

----

### OPKG配置
以下列出了 opkg 所使用的各个配置文件。opkg.conf 用于全局配置，customfeeds.conf 用于自定义仓库。其他配置文件的变更在系统升级时默认不被保留。

#### /etc/opkg.conf
```
dest root /
dest ram /tmp
lists_dir ext /var/opkg-lists
option overlay_root /overlay
option check_signature

# white iphone
option http_proxy http://192.168.8.103:1082/
```

#### /etc/opkg/customfeeds.conf
```
# add your custom package feeds here
#
# src/gz example_feed_name http://www.example.com/path/to/files
```

#### /etc/opkg/distfeeds.conf
```
src/gz openwrt_core http://downloads.openwrt.org/snapshots/targets/rockchip/armv8/packages
src/gz openwrt_base http://downloads.openwrt.org/snapshots/packages/aarch64_generic/base
src/gz openwrt_luci http://downloads.openwrt.org/snapshots/packages/aarch64_generic/luci
src/gz openwrt_packages http://downloads.openwrt.org/snapshots/packages/aarch64_generic/packages
src/gz openwrt_routing http://downloads.openwrt.org/snapshots/packages/aarch64_generic/routing
src/gz openwrt_telephony http://downloads.openwrt.org/snapshots/packages/aarch64_generic/telephony
```