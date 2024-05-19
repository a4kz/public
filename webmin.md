```
curl -o setup-repos.sh https://raw.githubusercontent.com/webmin/webmin/master/setup-repos.sh
```

```
sh setup-repos.sh
```

```
# centos
dnf install webmin
```

```
# debian
apt-get install webmin --install-recommends
```



### open port 1000 on centos

```
systemctl status firewalld
```

```
firewall-cmd --zone=public --add-port=10000/tcp --permanent
```

```
firewall-cmd --reload
```

```
# 一定要用 https 在浏览器中打开
https://a.b.c.d:e
```

