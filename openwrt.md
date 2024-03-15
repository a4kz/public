### IP 与 MAC 绑定
修改/etc/config/dhcp,增加如下的内容： 
```
# 不必重启，保存退出后立即生效
config host
  option ip ‘192.168.1.2’
  option mac ’00:11:22:33:44:55′
  option name ‘mypc’

config host
  option ...
  option ...
  option ...
```

### 在 Openwrt 中安装 docker

准备工作

- 在openwrt中挂载一个 `/opt` 分区作为储存Docker数据分区；
- 重启openwrt `reboot` 。 

安装过程

1. 手动更新软件包 `opkg update` ；
2. 手动安装Docker `opkg install docker` ，`opkg install dockerd` ；
3. 手动启动运行Docker `/etc/init.d/dockerd start` ；
4. 设置自启动，通过 `ssh` 输入  `ln -s /etc/init.d/dockerd /etc/rc.d/S100docker` 。 

