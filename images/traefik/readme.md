# Pure-FTPD Ready Docker Image

[Traefik](https://traefik.io/) is a reverse proxy / load balancer that's easy, dynamic, automatic, fast, full-featured, open source, production proven, provides metrics, and integrates with every major cluster technology...

Fork from [official Traefik image](https://github.com/containous/traefik)

## Building It

    docker build . -t traefik

## Starting It

Create **acme.json** file which will contain let's encrypt data :

    touch /data/acme.json && chmod 600 /data/acme.json

Starting it

    docker run -d --name traefik \
        -v /var/run/docker.sock:/var/run/docker.sock \
        -v /data/acme.json:/acme.json \
        -p 80:80 \
        -p 443:443 \
        -p 8080:8080 \
        traefik

## Testing It

    docker run -d --name whoami \
        -l traefik.backend=whoami \
        -l traefik.port=80 \
        -l traefik.enable=true \
        -l traefik.frontend.rule=Host:whoami.example.com \
        -l traefik.frontend.entryPoints=http,https \
        -l traefik.frontend.redirect.entryPoint=https \
        emilevauge/whoami

## Accessing the dashboard

    http://example.com:8080/dashboard/

## Removing It

    docker rm --force traefik