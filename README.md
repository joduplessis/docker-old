# Apache & PHP

This is a general run-of-mill Apache installation using PHP. Nice thing here is that you can specify a vhosts file. Useful with Symfony & Laravel.

```
docker build -t "repo:tag" .
docker run -p 80:80 -v $(pwd):/var/www/html repo:tag
```

# Nginx, PHP, Composer & MySQL
Useful holistic Compose file for Nginx.
```
docker compose up
```

# Docker

No files, but because I forget stuff.

```
docker run --rm -v $(pwd):/app composer/composer install
```
