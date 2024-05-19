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
https://a.b.c.d:e
```

