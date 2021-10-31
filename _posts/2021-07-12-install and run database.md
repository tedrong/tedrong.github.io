---
title: Install and run database
author: Ted Rong
date: 2021-07-12 22:21:00 +0800
categories: [Programing, Note]
tags: [database, docker]
math: true
mermaid: true
image:
  src: https://miro.medium.com/max/1400/1*C27c2zlHixp40boXTiEqTw.png
  width: 800
  height: 500
---

## Getting Images

### Postgres

```console
$ docker pull postgres
```

### Redis

```console
$ docker pull redis
```

## Create systemd service

### Make a executable script file

```console
$ sudo vim /usr/local/bin/docker-dev-database.sh
```

```bash
#!/bin/bash
docker run --rm --name postgreSQL -e POSTGRES_PASSWORD=docker -d -p 5432:5432 -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data postgres
docker run --rm -itd --name Redis -p 6379:6379 redis
```

### Create new service

Make a new service description at /etc/systemd/system/docker-dev-database.service

```bash
[Unit]
After=network.service

[Service]
ExecStart=/usr/local/bin/docker-dev-database.sh

[Install]
WantedBy=default.target
```

- Reload the service files to include the new service.
  
  `sudo systemctl daemon-reload`
- Start your service.
  
  `sudo systemctl start docker-dev-database.service`
- To check the status of your service.
  
  `sudo systemctl status docker-dev-database.service`
- To enable your service on every reboot.
  
  `sudo systemctl enable docker-dev-database.service`
- To disable your service on every reboot.
  
  `sudo systemctl disable docker-dev-database.service`