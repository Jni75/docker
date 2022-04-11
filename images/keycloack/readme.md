# Keycloack Docker Image

## Starting It

    docker run -d --name keycloack \
        -p 8080:8080 \
        -e KEYCLOAK_ADMIN=admin \
        -e KEYCLOAK_ADMIN_PASSWORD=admin \
        quay.io/keycloak/keycloak:latest \
        start-dev

## Removing It

    docker rm --force keycloack

