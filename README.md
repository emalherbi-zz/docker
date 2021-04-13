# docker

## Before installation

Before installation change this [line](https://github.com/emalherbi/docker-php-7/blob/master/docker-compose.yml#L10).

```yml
volumes:
  - /home/eduardo/Sites/docker/www:/var/www/html
```

## Installation

```bash
docker-compose up -d --build --force-recreate --remove-orphans
```
