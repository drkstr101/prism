# Stack

## About

This repository contains a traefik reverse proxy and a docker image to generate self-signed certificate for development projects.

## Requirements

- git
- docker
- docker compose
- make

## How to ?

### Clone the project

```shell
git clone git@github.com:devgine/stack.git
```

## Setup

```shell
make up
```

Visit traefik dashboard to make sure the installation is successfully done <https://dashboard.local.aps.org><br>
Or by visiting the api <https://dashboard.local.aps.org/api/rawdata>

> **Important**
> To use the traefik certificate your local domain must be a subdomain of _local.aps.org_<br>
> For example : _my_project.local.aps.org_

## Help

Run the following command to show all available jobs

```shell
make
```

## How to use services with traefik

Below is an example of using the nginx service with traefik

After running the nginx container, the service should be accessible by visiting <https://nginx.local.aps.org>

```yaml
services:
  nginx:
    container_name: nginx
    image: nginx:latest
    labels:
      - traefik.enable=true
      - traefik.docker.network=prism-net
      - traefik.http.routers.nginx-https.rule=Host(`nginx.local.aps.org`)
      - traefik.http.routers.nginx-https.entrypoints=websecure
      - traefik.http.routers.nginx-https.tls=true
      - traefik.http.services.nginx-loadbalancer.loadbalancer.server.port=80
    networks:
      - prism-net

networks:
  prism-net:
    external: true
```

## Chrome trust insecure local.aps.org

Open Chrome browser and visit the below URL then allow invalid certificates for resources loaded from local.aps.org.

```text
chrome://flags/#allow-insecure-local.aps.org
```
