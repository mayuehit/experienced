```shell
# 反向代理  https://www.cnblogs.com/quail2333/p/11188269.html

# 反向代理 404
看日志 error.log

妈的 ，是SELINUX这个鬼东西 搞了老子三个小时
setenforce 0
setsebool -P httpd_can_network_connect 1
```

```shell
server {
    listen     80;
    server_name   localhost;
    location / {
     proxy_pass http://192.168.10.45:8080;
    #    root   /opt/nginx/html;
     #   index  index.html index.htm;
   }
    #error_page  404              /404.html;

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /opt/nginx/html;
    }
}

```

