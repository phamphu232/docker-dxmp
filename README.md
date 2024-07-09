# Docker-dxmp

# Settings

```
cp .env.example .env
cp docker-compose.yml.example docker-compose.yml
docker compose up -d --build
```

# Useful commands line

```
# Copy configuration from docker image to host machine
docker run -it --name test1 --rm php:8.2.20-fpm-alpine3.20
docker cp test1:/usr/local/etc/php php8.2_copy

docker run -it --name test2 --rm httpd:alpine3.20
docker cp test2:/usr/local/apache2 apache2_copy

# Build image
docker build -t phamphu232/php:8.2.20-fpm-alpine3.20 -f ./php8.2/Dockerfile .
docker push phamphu232/php:8.2.20-fpm-alpine3.20
```