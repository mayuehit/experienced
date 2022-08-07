```shell
upstream html {
   server 192.168.10.45:8080;
   server 192.168.10.93:8080;
}
server {
    listen     80;
 #   listen  443 ssl;
    server_name   localhost;
 #   ssl on;
 #   ssl_certificate /opt/nginx/ssl/server.crt;
 #   ssl_certificate_key /opt/nginx/ssl/server.key;
 #   ssl_session_timeout 5m;
   # access_log  /var/log/nginx/host.access.log  main;
    location / {
     proxy_pass http://html;
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

