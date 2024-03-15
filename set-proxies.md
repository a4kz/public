## Windows

```
// 仅仅是对command prompt的代理，不是对所有command的全局代理
// 因此，其实的command需要单独设置
set HTTP_PROXY=http://user:password@proxy.domain.com:port
```

#### cmder
```
Set http_proxy=http://[proxy]:[port]
Set https_proxy=http://[proxy]:[port]
```

#### bash
```
export http_proxy=http://[proxy]:[port]
export https_proxy=http://[proxy]:[port]
```

#### Powershell
```
$env:http_proxy=http://[proxy]:[port]
$env:https_proxy=http://[proxy]:[port]
```

## Git

```
git config --global http.proxy http://proxy:port
```

## npm

```
npm config set proxy http://proxy:port
```
```
// 代理如果不起作用
// Cache data in your computer is broken. Try this:

npm cache clean --force

// 取消
npm config delete proxy
npm config delete https-proxy
```
```
// 查看某个package的所有版本
npm view joi versions
npm view joi versions --json
```

```


For some weird reasons, none of these answers helped me. I discovered it was an issue with my proxy. I solved it following these steps:

npm cache clean --force

npm config rm proxy

npm config rm https-proxy

npm cache verify

Delete the node_modules folder and run

npm install

```



## yarn

```
yarn config set proxy http;//proxy:port
```

### docker

```
vi ~/.docker/config.json
```

```
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://127.0.0.1:3001",
     "httpsProxy": "http://127.0.0.1:3001",
     "noProxy": "*.test.example.com,.example2.com,127.0.0.0/8"
   }
 }
}
```

### centOS

```
# ??? apply to all logged-in users
/etc/profile.d/proxy.sh
```

```
vi /etc/profile
```

```
# set proxy config via profie.d - should apply for all users
# 
PROXY_URL="http://10.10.1.10:8080/"

export http_proxy="$PROXY_URL"
export https_proxy="$PROXY_URL"
export ftp_proxy="$PROXY_URL"
export no_proxy="127.0.0.1,localhost"

# For curl
export HTTP_PROXY="$PROXY_URL"
export HTTPS_PROXY="$PROXY_URL"
export FTP_PROXY="$PROXY_URL"
export NO_PROXY="127.0.0.1,localhost"
```

```
$ source /etc/profile
$ env | grep -i proxy
```

```
# dnf
vi /etc/dnf/dnf.confg
proxy=http://10.10.1.10:8080

# yum
vi /etc/yum.conf
proxy=http://10.10.1.10:8080
```

### ubuntu

```
# ??? apply to all logged-in users
/etc/profile.d/proxy.sh
```

```
# set proxy config via profie.d - should apply for all users
# 
export http_proxy="http://10.10.1.10:8080/"
export https_proxy="http://10.10.1.10:8080/"
export ftp_proxy="http://10.10.1.10:8080/"
export no_proxy="127.0.0.1,localhost"

# For curl
export HTTP_PROXY="http://10.10.1.10:8080/"
export HTTPS_PROXY="http://10.10.1.10:8080/"
export FTP_PROXY="http://10.10.1.10:8080/"
export NO_PROXY="127.0.0.1,localhost"
```

```
sudo chmod +x  /etc/profile.d/proxy.sh
$ source /etc/profile.d/proxy.sh
$ env | grep -i proxy
```

```
# apt
$ sudo nano /etc/apt/apt.conf.d/80proxy

Acquire::http::proxy "http://10.10.1.10:8080/";
Acquire::https::proxy "https://10.10.1.10:8080/";
Acquire::ftp::proxy "ftp://10.10.1.10:8080/";
```

```
$ vim ~/.wgetrc                           
use_proxy = on
http_proxy = http://10.10.1.10:8080/ 
https_proxy = http://10.10.1.10:8080/ 
ftp_proxy = http://10.10.1.10:8080/ 
```

