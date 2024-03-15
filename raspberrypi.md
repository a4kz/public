### 用raspberry pi官方烧录软件烧录就可以，注意设置好高级选项就好了，地区、时区按照实际来

### 远程登录

- 手动写入 ssh 空文件 ??
- `ssh username@raspberrypi.local`
- `ssh username@raspberrypi`

### 如果只能通过 IP 远程登录，想使用主机登录怎么办？
```
sudo apt-get install avahi-daemon
```

```
vi /etc/avahi/services/multiple.service
```

```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
        <name replace-wildcards="yes">%h</name>
        <service>
                <type>_device-info._tcp</type>
                <port>0</port>
                <txt-record>model=RackMac</txt-record>
        </service>
        <service>
                <type>_ssh._tcp</type>
                <port>22</port>
        </service>
</service-group>
```

```
sudo /etc/init.d/avahi-daemon restart
```



### 给  Debian / Pi  重新命名

```
sudo -s

hostnamectl set-hostname new_server_name

vi /etc/hosts # 修改最后一行

hostnamectl # 修改完成后检查一下
```

### 修改用户密码

```
sudo -s
sudo passwd username
```


### 全局代理

```
# .bashrc
export http_proxy="http://127.0.0.1:8123"
export https_proxy="http://127.0.0.1:8123"
source /root/.bashrc
```



