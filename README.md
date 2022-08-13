
# LeetCode Judge Deploy

- Docker compose v1: `docker-compose`
- Docker compose v2: `docker compose`

## Prepare the configuration

```shell
$ cp .env.example .env
$ vi .env


$ cp .env.app.example .env.app
$ vi .env.app
```

```shell
# Pull all services images.
$ docker compose pull

# Start MinIO(S3) service.
$ docker compose up minio -d
```

### Setup MinIO(S3) bucket

1. Open [`http://localhost:9090`](http://localhost:9090).
2. Click `Buckets`, `http://localhost:9090/buckets`.
3. Click `Create Bucket`, `http://localhost:9090/buckets/add-bucket`.
4. Key in `Bucket Name` and Click `Create Bucket`.
5. `$ vi .env.app`, Edit env
```
AWS_ACCESS_KEY_ID=${MINIO_ROOT_USER}
AWS_SECRET_ACCESS_KEY=${MINIO_ROOT_PASSWORD}
AWS_S3_ENDPOINT_URL=http://minio:9000
AWS_STORAGE_BUCKET_NAME=${MINIO_BUCKET_NAME}
```

## Installtion

```shell

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