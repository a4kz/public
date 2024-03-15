### 安装 oh-my-zsh / linux 和 mac都适用
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
