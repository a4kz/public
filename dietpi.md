### 动态mac改成静态mac, `/etc/network/interfaces`

```
auto enp3s0
iface enp3s0 inet static
    address 192.0.2.7
    netmask 255.255.255.0
    gateway 192.0.2.254
    hwaddress ether 00:11:22:33:44:55
```

```
allow-hotplug enp3s0
iface enp3s0 inet dhcp
    hwaddress ether 00:11:22:33:44:55
```

### 使用 `dietpi-config`配置，不要 `apt upgrade`升级！	
