# Pure-FTPD Ready Docker Image

Fork from https://github.com/stilliard/docker-pure-ftpd

With options :

- 50 max clients at once    
- 20 max requests per IP
- No anonymous
- No chmod
- No TLS

## Building It

    docker build . -t pure-ftpd

## Starting It

    docker run -d --name pure-ftpd \
        -v /data/user:/data \
        -v /data/pure-ftpd/passwd:/etc/pure-ftpd/passwd/ \
        -e PUBLICHOST=exemple.com \
        -e FTP_USER_NAME=username \
        -e FTP_USER_PASS=password \
        -e FTP_USER_HOME=/data \
        -e FTP_USER_UID=uid \
        -e FTP_USER_GID=gid \
        -e FTP_PASSIVE_PORTS=30000:30100 \
        -p 21:21 \
        -p 30000-30100:30000-30100 \
        pure-ftpd

See https://github.com/stilliard/docker-pure-ftpd for parameters detail

## Removing It

    docker rm --force pure-ftpd