```shell
# 参考博客
https://www.pianshen.com/article/78541408453/
# 安装nginx
sudo rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum install -y nginx
# 80端口访问不了 ，清除所有防火墙规则   
iptables -F

# 端口无法设置为31945 查看http允许访问的端口
 semanage port -l | grep http_port_t
 # 添加端口
 semanage port -a -t http_port_t -p tcp 31945

# ping 抓包
tcpdump -i ens33 icmp -n


```

```

  # listen      31945;
    listen  443 ssl;
    server_name  www.changeit.com;
    ssl on;
    ssl_certificate /opt/nginx/ssl/server.crt;
    ssl_certificate_key /opt/nginx/ssl/server.key;
    ssl_session_timeout 5m;
    access_log  /var/log/nginx/host.access.log  main;
       location / {
       root   /opt/nginx/html;
       index  index.html index.htm;
   }
```

