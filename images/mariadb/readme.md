# MariaDB Docker Image

Fork from https://github.com/bianjp/docker-mariadb-alpine

## Building It

    docker build . -t mariadb

## Starting It

    docker run -d --name mariadb \
        -v /data/mariadb:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=password \
        mariadb

## Accessing It

    docker exec -it mariadb mysql -uroot --password="password"

## Removing It

    docker rm --force mariadb

