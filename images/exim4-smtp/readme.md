# Pure-FTPD Ready Docker Image

SMTP server for internal use (by the containers)

Fork from https://github.com/namshi/docker-smtp

## Building It

    docker build . -t smtp

## Starting It

Retrieve network subnet :

    docker network inspect bridge

Sample :

    [
        {
            "Name": "bridge",
            "Id": "72aed082cad51014ded6339eedfb407db615d62fce3d51085ab55602a6c7c020",
            "Created": "2018-06-12T21:29:29.263028322+02:00",
            "Scope": "local",
            "Driver": "bridge",
            "EnableIPv6": false,
            "IPAM": {
                "Driver": "default",
                "Options": null,
                "Config": [
                    {
                        "Subnet": "172.17.0.0/16",
                        "Gateway": "172.17.0.1"
                    }
                ]
            },
            "Internal": false,
            "Attachable": false,
            "Ingress": false,
            "ConfigFrom": {
                "Network": ""
            },
            "ConfigOnly": false,
            "Containers": {},
            "Options": {
                "com.docker.network.bridge.default_bridge": "true",
                "com.docker.network.bridge.enable_icc": "true",
                "com.docker.network.bridge.enable_ip_masquerade": "true",
                "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
                "com.docker.network.bridge.name": "docker0",
                "com.docker.network.driver.mtu": "1500"
            },
            "Labels": {}
        }
    ]

Starting it with allowed relay networks

    docker run -d --name smtp \
        -e MAILNAME=exemple.com \
        -e RELAY_NETWORKS=:172.17.0.0/16 \
        smtp

## Removing It

    docker rm --force smtp

