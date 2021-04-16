# docker

## Before installation

Before installation change this [line](https://github.com/emalherbi/docker/blob/main/docker-compose.yml).

```yml
volumes:
  - /home/eduardo/Sites/www:/var/www/html
```

## Installation

```bash
docker-compose up -d --build --force-recreate --remove-orphans
```
