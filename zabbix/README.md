## Zabbix
This example provides a base setup for using [Zabbix](https://www.zabbix.com/).
More details on how to customize the installation and the compose file can be found in [zabbix documentation](https://www.zabbix.com/documentation/current/en/manual/installation/containers).

Project structure:
```
.
├── compose.yaml
└── README.md
```

## Download
```
wget https://raw.githubusercontent.com/AndreyBrigunet/docker-compose/master/zabbix/compose.yml
```


## Deploy with docker compose
When deploying this setup, the web interface will be available on port 80 (e.g. http://localhost:80).

``` shell
$ docker compose up -d
Starting portainer ... done
```


## Expected result

Check containers are running:
```
$ docker ps
CONTAINER ID   IMAGE                           COMMAND                  CREATED          STATUS                          PORTS                                                                                  NAMES
860311c00e62   portainer/portainer-ce:alpine   "/portainer -H unix:…"   54 seconds ago   Up 53 seconds                   8000/tcp, 0.0.0.0:9000->9000/tcp, :::9000->9000/tcp                                    portainer

```

Navigate to `http://localhost:9000` in your web browser to access the portainer web interface and create an account.


Stop the containers with
``` shell
$ docker compose down
# To delete all data run:
$ docker compose down -v
```
