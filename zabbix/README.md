## Zabbix
This example provides a base setup for using [Zabbix](https://www.zabbix.com/).
More details on how to customize the installation and the compose file can be found in [zabbix documentation](https://www.zabbix.com/documentation/current/en/manual/installation/containers).

Project structure:
```
.
├── compose.yaml
└── README.md
```

## Install Docker
```
sudo apt update
sudo apt upgrade
sudo apt install docker.io
sudo apt install docker-compose
```

## add timezone on sistem
```
mkdir -p /var/lib/zabbix/
ln -sf /usr/share/zoneinfo/Europe/Chisinau /var/lib/zabbix/localtime
echo 'Europe/Chisinau' > /var/lib/zabbix/timezone
```

## Download
```
wget https://raw.githubusercontent.com/AndreyBrigunet/docker-compose/master/zabbix/compose.yml
```


## Deploy with docker compose
When deploying this setup, the web interface will be available on port 80 (e.g. http://localhost:80).

``` shell
$ docker-compose up -d
Creating network "root_zabbix-net" with driver "bridge"
Creating root_zabbix-agent_1 ... done
Creating zabbix-postgres     ... done
Creating zabbix-server       ... done
Creating zabbix-web          ... done
```


## Expected result

Check containers are running:
```
$ docker ps
CONTAINER ID   IMAGE                                         COMMAND                  CREATED          STATUS          PORTS                                                                            NAMES
eda431ff128b   zabbix/zabbix-web-nginx-pgsql:alpine-latest   "docker-entrypoint.sh"   37 seconds ago   Up 37 seconds   0.0.0.0:80->8080/tcp, :::80->8080/tcp, 0.0.0.0:443->8443/tcp, :::443->8443/tcp   zabbix-web
6a102987d453   zabbix/zabbix-server-pgsql:alpine-latest      "/sbin/tini -- /usr/…"   38 seconds ago   Up 37 seconds   0.0.0.0:10051->10051/tcp, :::10051->10051/tcp                                    zabbix-server
7351a3ce4edd   postgres:alpine                               "docker-entrypoint.s…"   39 seconds ago   Up 38 seconds   5432/tcp                                                                         zabbix-postgres
3a12b3ef4759   zabbix/zabbix-agent:latest                    "/sbin/tini -- /usr/…"   39 seconds ago   Up 39 seconds                                                                                    root_zabbix-agent_1
```

Navigate to `http://localhost:80` in your web browser to access the portainer web interface and create an account.


Stop the containers with
``` shell
$ docker-compose down
# To delete all data run:
$ docker-compose down -v
```

## Login
```
login: Admin
password: zabbix
```
