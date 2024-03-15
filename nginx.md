### 在nginx中，想把任何https不访问根目录的请求，重新定向到访问根目录，如何解决？

要实现在nginx中将任何https请求重定向到根目录，您可以使用以下配置指令，if语句可能会让nginx性能变差：

```
server {
    listen       443 ssl;
    server_name  example.com;

    # SSL证书配置
    ssl_certificate      /path/to/cert.crt;
    ssl_certificate_key  /path/to/cert.key;

    # 根目录重定向
    if ($request_uri != '/') {
        return 301 https://$server_name/;
    }

    # 其他配置项
    ...
}
```

