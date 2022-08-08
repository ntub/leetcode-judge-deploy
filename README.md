
# LeetCode Judge Deploy

- Docker compose v1: `docker-compose`
- Docker compose v2: `docker compose`

## Prepare the configuration

```shell
$ cp .env.example .env
$ vi .env


$ cp .env.app.example .env
$ vi .env.app
```

## Installtion

```shell
# Pull all services images.
$ docker compose pull

# Run all services.
$ docker compose up -d

# Show `app` service log.
$ docker compose logs -f app

# Load `app` service data to DB.
$ docker compose exec app python manage.py loaddata problems -v 3 -i
```

## Open Website

- Admin Page: [`http://localhost:8000/admin/`](http://localhost:8000/admin/)
- API Documents : [`http://localhost:8000/api/docs`](http://localhost:8000/api/docs)
- Base API URL: `http://localhost:8000/api/v1`

## Remove containers

```shell
$ docker compose down
```