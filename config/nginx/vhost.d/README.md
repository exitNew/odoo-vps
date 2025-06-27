Add your domain name here

```
(example: nginx/vhost.d/www.domain.com)
touch www.domain.com domain.com
```

```
# add this inside www.domain.com and domain.com
# config your odoo.conf

location /longpolling {
    return 307 /websocket;
}

location /websocket {
    proxy_pass http://odoo:8072;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_read_timeout 720s;
    proxy_connect_timeout 720s;
    proxy_buffering off;
}

map $http_upgrade $connection_upgrade {
  default upgrade;
  ''      close;
}

```

Restart nginx-proxy

```
docker compose -f docker-compose-nginx.yaml restart nginx-proxy
```

Re check the domain

```
docker exec nginx-proxy cat /etc/nginx/conf.d/default.conf | grep server_name
```
