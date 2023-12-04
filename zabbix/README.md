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

## Download
```
wget https://raw.githubusercontent.com/AndreyBrigunet/docker-compose/master/zabbix/compose.yml
```


## Deploy with docker compose
When deploying this setup, the web interface will be available on port 80 (e.g. http://localhost:80).

``` shell
$ docker-compose up -d
Starting root_zabbix-agent_1    ... done
Starting root_adminer_1         ... done
Starting root_postgres-server_1 ... done
Starting root_zabbix-server_1   ... done
Starting root_zabbix-web_1      ... done
```


## Expected result

Check containers are running:
```
$ docker ps
CONTAINER ID   IMAGE                                         COMMAND                  CREATED         STATUS                        PORTS                                                       NAMES
ac3ecf804815   zabbix/zabbix-web-nginx-pgsql:ubuntu-latest   "docker-entrypoint.sh"   2 minutes ago   Up About a minute             8080/tcp, 8443/tcp, 0.0.0.0:8090->80/tcp, :::8090->80/tcp   root_zabbix-web_1
0143438f1a2f   zabbix/zabbix-server-pgsql:ubuntu-latest      "/usr/bin/tini -- /u…"   2 minutes ago   Restarting (1) 1 second ago                                                               root_zabbix-server_1
5ae941ed4719   zabbix/zabbix-agent:latest                    "/sbin/tini -- /usr/…"   2 minutes ago   Up About a minute                                                                         root_zabbix-agent_1
0fc6abe8708b   postgres:latest                               "docker-entrypoint.s…"   2 minutes ago   Up About a minute             5432/tcp                                                    root_postgres-server_1
f0dc4bcb8bbf   adminer                                       "entrypoint.sh php -…"   2 minutes ago   Up About a minute             0.0.0.0:8080->8080/tcp, :::8080->8080/tcp                   root_adminer_1
```

Navigate to `http://localhost:9000` in your web browser to access the portainer web interface and create an account.


Stop the containers with
``` shell
$ docker-compose down
# To delete all data run:
$ docker-compose down -v
```
