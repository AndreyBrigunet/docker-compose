## Plex
This example provides a base setup for using [Plex](https://www.plex.tv/).
More details on how to customize the installation and the compose file can be found in [linuxserver documentation](https://github.com/linuxserver/docker-plex).
Alternatively, you can use different plex images (e.g. official plex image by [plexinc](https://github.com/plexinc/pms-docker))


Project structure:
```
.
├── compose.yaml
└── README.md
```

[_compose.yaml_](compose.yaml)
``` yaml
services:
  plex:
    image: linuxserver/plex:latest
```

## Deploy with docker compose
When deploying this setup, the web interface will be available on port 32400 (e.g. http://localhost:32400/web).

``` shell
$ docker compose up -d
Starting plex ... done
```


## Expected result

Check containers are running:
```
$ docker ps
CONTAINER ID   IMAGE                             COMMAND                  CREATED          STATUS         PORTS                                          NAMES
62fc3ff1f1a0   linuxserver/plex:latest           "/init"                  38 seconds ago   Up 3 seconds                                                  plex
```

Navigate to `http://localhost:32400/web` in your web browser to access the plex web interface.


Stop the containers with
``` shell
$ docker compose down
# To delete all data run:
$ docker compose down -v
```
