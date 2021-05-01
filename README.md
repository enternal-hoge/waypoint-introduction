# waypoint-introduction

I tried the first step of waypoint.

## Prerequirement

- Docker Desktop
- brew(for mac)

## Install Waypoint CLI

Install waypoint cli tool.

```bash
$ brew tap hashicorp/tap
$ sudo chown -R $(whoami) /usr/local/lib/pkgconfig
$ chmod u+w /usr/local/lib/pkgconfig
$ brew install hashicorp/tap/waypoint
$ waypoint version
CLI: v0.3.1 (b550e5ce)
```

## Install Waypoint Server Locally

Install waypoint server using docker.

```bash
$ docker pull hashicorp/waypoint:latest
$ waypoint install -platform=docker -accept-tos
```

confirm.

```bash
$ docker images
REPOSITORY                                 TAG                 IMAGE ID            CREATED             SIZE
...
hashicorp/waypoint                         latest              03439ba3c8ec        10 days ago         290MB
...

$ docker ps -a
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS                    PORTS                              NAMES
...
20b5ad61e781        hashicorp/waypoint:latest       "/usr/bin/waypoint r…"   2 minutes ago       Up 2 minutes                                                 waypoint-runner
54254cd2321f        hashicorp/waypoint:latest       "/usr/bin/waypoint s…"   2 minutes ago       Up 2 minutes              0.0.0.0:9701-9702->9701-9702/tcp   waypoint-server
...

$ netstat -an | grep 9701
tcp46      0      0  *.9701                 *.*                    LISTEN     

$ netstat -an | grep 9702
tcp46      0      0  *.9702                 *.*                    LISTEN     
```

## Access Local Server

Access own your browser.

https://localhost:9702


Click Autenticate.

![01](./img/01.jpg)

Execute following command. and copy token string.

```bash
$ waypoint token new
bM152PWkXxfoy4vA51JFhR7LpcXSqtvXHGHaHnapPx1VY86HXJK7vG9ytXiDaHhffD5CAi3amJbCdvZ7nv5CpD6h1qTWVmCNXEksA
```

Paste token string and Authencated with Token Button.

![02](./img/02.jpg)


Logged in.

![03](./img/03.jpg)


## First Project Deploy

TBD

## Reference

https://learn.hashicorp.com/tutorials/waypoint/get-started-install