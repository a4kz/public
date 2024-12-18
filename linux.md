### 安装 oh-my-zsh / linux 和 mac都适用
__如果系统时间不正确，那么 apt 将无法更新__

### Debian设置系统级别的代理：[参考文章](https://computingforgeeks.com/how-to-set-system-proxy-on-debian-linux/)

```
vi /etc/profile.d/proxy.sh
```

```
export http_proxy="http://A.B.C.D:E/"
export https_proxy="http://A.B.C.D:E/"
export ftp_proxy="http://A.B.C.D:E/"
export no_proxy="127.0.0.1,localhost"
```

```
chmod +x /etc/profile.d/proxy.sh
```

```
logout
```
### debian 12 sources.list: /etc/apt/sources.list

```
deb https://deb.debian.org/debian/ bookworm contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ bookworm contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ bookworm-updates contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ bookworm-updates contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ bookworm-proposed-updates contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ bookworm-proposed-updates contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ bookworm-backports contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ bookworm-backports contrib main non-free non-free-firmware

deb https://security.debian.org/debian-security/ bookworm-security contrib main non-free non-free-firmware
# deb-src https://security.debian.org/debian-security/ bookworm-security contrib main non-free non-free-firmware
```


#### 确认查看代理是否起作用
```
env | grep -i proxy
```


```
apt update
```
```
apt install zsh
```

```
wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh && sh install.sh
```

### 更新 oh-my-zsh

```
omz update
```

### 安装 zsh-autosuggestions

```
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/zsh-autosuggestions
```
```
vi ~/.zshrc
```


```
ZSH_THEME="mortalscumbag"
```

#### 写到 `~/.zshrc`
```
source ~/.oh-my-zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```
```
source /etc/profile.d/proxy.sh
```
#### 退出 `~/.zshrc`后
```
source ~/.zshrc
```
### Debian / Ubuntu修改主机名

```
ssh root@server
su - root
hostnamectl set-hostname new_name
vi /etc/hosts
hostnamectl
```

### 禁用ipv6 `/etc/sysctl.conf`

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

```
sudo sysctl -p
```

### Ubuntu / Debian 允许 root ssh 登录

```
# /etc/ssh/sshd_config

PermitRootLogin yes
PasswordAuthentication yes
```

```
systemctl restart sshd
```

### 安装 docker

```
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
```

### 设置 docker 代理: 即使前面设置了系统级的代理，此处docker还是需要设置

```
mkdir /etc/systemd/system/docker.service.d
```
#### 创建文件 `/etc/systemd/system/docker.service.d/http-proxy.conf `

```
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/"
Environment="HTTPS_PROXY=http://proxy.example.com:80/"
Environment="NO_PROXY=localhost,127.0.0.0/8,docker-registry.somecorporation.com"
```
```
systemctl daemon-reload
```

```
systemctl restart docker
```

### 设置代理 `/etc/environment` Debian不起作用

```
export http_proxy="http://a.b.c.d:e/"
```


### 修改为指定时间, DietPi不修改apt无法更新
```
date -s  "YYYY/MM/DD hh:mm:ss"

date -s "2024/04/09 16:06:32"
```

__其他修改时间方法__

```
timedatectl
timedatectl list-timezones
timedatectl list-timezones | grep AAA
timedatectl set-timezone AAA/XYZ
```




### CasaOS

```
wget -qO- https://get.casaos.io | bash
```

```
casaos-uninstall
```
#### update
```
curl -fsSL https://get.casaos.io/update |  bash
```



### Debian ipv4 自动消失问题的解决

#### 某些设备只能通过DHCP静态的方式修改，以下方法将不起作用

```
vi /etc/network/interfaces
```

```
iface enp0s3 inet static
address 192.168.1.183
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 1.1.1.1
```

#### /etc/config/network 如果不对，需要修改这个位置的文件

__保存并退出后：__

```
systemctl restart networking.service
```

### 给 `yum` / `dnf` 设置代理, 设置`/etc/environment`不起作用

```
# /etc/dnf/dnf.conf
# global
proxy=http://a.b.c.d:e/

# optional
proxy_username=ffff
proxy_password=gggg
```
```
# user level
# .bash_profile

export http_proxy=http://a.b.c.d:e/
export https_proxy=Http://a.b.c.d:e/

export http_proxy=http://username:password@a.b.c.d:e/
```
### Kali enable ssh
```
# /etc/ssh/sshd_config

PermitRootLogin yes
```


### dietpi

```
# set a proxy
# .bashrc
# 在/etc/environment 中设置不起作用
export http_proxy="http://a.b.c.d:e/"
epxort https_proxy="http://a.b.c.d:e/"
```

```
# .bashrc	中设置时间 ???
export TZ="AAA/BBB"
```

### PVE
#### /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on"
```



#### 安装 istoreos
- 上传 img

- 创建虚拟机

- 不使用任何介质

- SCSI控制器：VirtIO SCSI

- 删除 磁盘

- CPU: host

- 内存：2048

- 网络：VirtIO

- 启动后输入

  ```
  qm importdisk [istore-id] /var/lib/vz/template/iso/iStoreOS.img local-lvm
  ```
  
- 硬件 -> 点开 未使用的磁盘 -> 添加

- 选项 -> 引导顺序 -> 只对 scsi0 打勾

- 设置成静态ip后 reboot 

### macOS禁用 ipv6

```
sudo networksetup -listallnetworkservices
```

```
sudo networksetup -setv6off Wi-Fi
```

```
sudo networksetup -setv6off Ethernet
```

#### 重新启用 ipv6

```
sudo networksetup -setv6automatic Wi-Fi
```

```
sudo networksetup -setv6automatic Ethernet
```

#### npm proxy


##### For HTTP:
```
npm config set proxy http://proxy_host:port
```

##### For HTTPS:
```
npm config set https-proxy http://proxy.company.com:8080
```

### 定位大文件位置

```
sudo du -sh /path/to/large/file/* | sort -rh | head -n 10
```

