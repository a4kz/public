### 安装 oh-my-zsh / linux 和 mac都适用
__如果系统时间不正确，那么 apt 将无法更新__
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
```
source ~/.oh-my-zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```

### Debian / Ubuntu修改主机名

```
ssh root@server
su - root
hostnamectl set-hostname new_name
vi /etc/hosts
hostnamectl
```

### 安装 docker

```
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
```

### 设置代理 `/etc/environment`

```
export http_proxy="http://a.b.c.d:e/"
```


### 修改为指定时间, DietPi不修改apt无法更新
```
date -s  "YYYY/MM/DD hh:mm:ss"

date -s "2024/04/09 16:06:32"
```

### CasaOS

```
wget -qO- https://get.casaos.io | sudo bash
```

```
casaos-uninstall
```

