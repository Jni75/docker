# Docker Tips

## Delete all containers

    docker rm --force $(docker ps -a -q)

## Delete all images

    docker rmi $(docker images -q)

## Delete all &lt;none&gt; images

    docker rmi $(docker images --filter "dangling=true" -q --no-trunc)

## Truncate containers logs

    truncate -s 0 /var/lib/docker/containers/*/*-json.log

## Delete unsed volumes

    docker volume rm $(docker volume ls -qf dangling=true)

## Cleaning up unused objects

    docker system prune