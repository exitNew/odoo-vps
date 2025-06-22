# 1. Install Docker CE

```
sudo apt update
sudo apt upgrade
```

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
```

```
apt-cache policy docker-ce
```

```
sudo apt install docker-ce docker-ce-cli containerd.io
```

```
sudo systemctl status docker
```

# 2. Setup Password env

```
# Install if you don't have it: sudo apt install apache2-utils
htpasswd -nb admin 'MyStr0ngP@ssw0rd!'

`admin:<the hash>`

# Then add it on .env
TRAEFIK_DASHBOARD_USER as admin
TRAEFIK_DASHBOARD_PASS_HASH as <the hash>
```


# 3. Add on addons folder



# 4. Chmod letsencrypt

if you using docker-compose-traefik.yaml you dont have to do this


# 5. Create Cert for nginx (if you use nginx)

if you using docker-compose-traefik.yaml you dont have to do this



# 6. RUN

```
docker-compose -f docker-compose-nginx.yaml up -d

# or
docker-compose -f docker-compose-nginx.yaml up --build -d
```

# 7. Prometheus, grafana, alertmanager


```
	•	Traefik: https://your-domain/traefik
	•	Prometheus: http://your-server:9090
	•	Alertmanager: http://your-server:9093
	•	Grafana: http://your-server:3000 (login: admin / admin)

```
