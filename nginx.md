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

---

$ wget http://nginx.org/download/nginx-a.b.c.tar.gz
$ tar zxvf nginx-a.b.c.tar.gz
$ ls
$ ./configure --prefix=/usr/local/nginx

# 缺少pcre

$ yum install pcre pcre-devel
$ make && make install
$ cd /usr/local/nginx

---

$ nginx -s stop

# stop nginx 

$ ps aux | grep nginx

# aux: all usage x

# systemd

/lib/systemd/system/nginx.service

# 启动

$ systemctl start nginx

# 停止

$ systemctl stop nginx

# 开机运行

$ systemctl enable nginx

$ systemctl status nginx

/etc/nginx.conf

# 定义虚拟主机

events {

}

http {
	types {
		text/html html;
		text/css css;
	}
	

	# include mine.types;
	
	server {
		listen 80;
		server_name: 192.168.26.133;
		root /home/kevin/sites/demo;
		
		location /greet {
			return 200 'Hello from Nginx "/greet" location';
		}
		
		# 或者
		# = 完全匹配
		# ～ 匹配正则表达式
		# ～* 匹配的正则表达式不区分大小写
		# ^~ 优先前缀匹配
		location = /greet {
			return ...
		}
	}

}

$ nginx -t

cat /etc/nginx/mime.types
types {
	text/html html htm shtml;
	text/css css;
	text/xml xml;
	.....
}

1. Exact Match
   =

2. Preferential Prefix Match
   ^~

3. REGEX Match
   ～ 正则表达式
   ~* 不区分大小写的正则表达式

4. Prefix Match
   不需要标记

Variables

location /inspect {
	return 200 "$host\n$uri\n$args";
	# return 200 "Name: $arg_name";
}

# check static API key

if ( $arg_apikey != 1234 ) {
	return 401 "Incorrect api key.";
}

=========

set $weekend 'No';
if ($date_local  ~ 'Saturday|Sunday') {
	set $weekend "Yes"
}

location /is_weekend {
	return 200 $weekend;
}

location /logo {
	return 307 /thumb.png;
}

=============

nginx.conf

events {}

http {
	include mime.types;
	

	server {
		listen 80;
		server_name 192.168.26.133;
		
		root /home/kevin/sites/demo;
		rewrite ^/user/\w+ /greet;
		
		location /greet {
			return 200 "Hello User";
		}
	}

}

===============
user www-data;

worker_processes auto;

events {
	worker_connections 1024;
}

http {
	include mine.types;
	

	server {
		listen 80;
		server_name 192.168.26.133;
		
		root /home/kevin/sites/demo;
		
		try_files $uri /cat.png /greet;
		index index.php index.html;
		
		location /greet {
			return 200 "Hello User!";
		}
		
		location ~\.php$ {
			include fastcgi.conf;
			fastcgi_pass unix:/run/php/php7.1-fpm.sock;
		}
	}

}

