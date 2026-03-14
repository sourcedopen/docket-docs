# Open Docket

A ticket management system for tracking complaints, grievances, and support workflows. Built with Laravel.

## Requirements

| Dependency | Required | Notes |
|---|---|---|
| **MySQL or PostgreSQL** | Yes | Any version supported by Laravel 12 |
| **Redis** | If using Horizon | Powers queues, cache, and session when enabled |
| **S3-compatible storage** | No | Falls back to local private disk if not configured |

## Installation (Docker)

Open Docket publishes a Docker image to GitHub Container Registry.

```
ghcr.io/sourcedopen/docket:latest
```

### 1. Pull the image

```bash
docker pull ghcr.io/sourcedopen/docket:latest
```

### 2. Configure environment variables

Copy the example below or mount your own `.env` file. At minimum you need to set:

| Variable | Description |
|---|---|
| `APP_KEY` | Laravel encryption key. Generate with `php artisan key:generate --show` |
| `APP_URL` | Public URL of your installation |
| `DB_CONNECTION` | `mysql` or `pgsql` |
| `DB_HOST` | Database hostname |
| `DB_PORT` | Database port (`3306` for MySQL, `5432` for PostgreSQL) |
| `DB_DATABASE` | Database name |
| `DB_USERNAME` | Database user |
| `DB_PASSWORD` | Database password |

#### Optional: Redis

| Variable | Description |
|---|---|
| `REDIS_HOST` | Redis hostname |
| `REDIS_PORT` | Redis port (default `6379`) |
| `REDIS_PASSWORD` | Redis password (default `null`) |
| `QUEUE_CONNECTION` | Set to `redis` to enable background jobs |
| `CACHE_STORE` | Set to `redis` for Redis-backed cache |
| `SESSION_DRIVER` | Set to `redis` for Redis-backed sessions |

#### Optional: S3-compatible storage

If not configured, file uploads are stored on the local private disk.

| Variable | Description |
|---|---|
| `FILESYSTEM_DISK` | Set to `s3` to use S3 storage |
| `MEDIA_DISK` | Set to `s3` for media library uploads |
| `AWS_ACCESS_KEY_ID` | S3 access key |
| `AWS_SECRET_ACCESS_KEY` | S3 secret key |
| `AWS_DEFAULT_REGION` | S3 region |
| `AWS_BUCKET` | S3 bucket name |
| `AWS_ENDPOINT` | Custom endpoint for MinIO or other S3-compatible services |
| `AWS_URL` | Public URL prefix for the bucket |
| `AWS_USE_PATH_STYLE_ENDPOINT` | Set to `true` for MinIO |

### 3. Run database migrations

```bash
docker exec -it docket php artisan migrate --force
```

### 4. Create your first user

```bash
docker exec -it docket php artisan users:create
```

### 5. (Optional) Seed default ticket types

```bash
docker exec -it docket php artisan db:seed --class=TicketTypeSeeder --force
```

## Reference Docker Compose

A complete `docker-compose.yml` is provided in the repository at [`docker-compose.yml`](docker-compose.yml) for reference. It includes:

- **app** — Open Docket application
- **mysql** — MySQL 8 database
- **redis** — Redis for queues, cache, and sessions
- **minio** — S3-compatible object storage (optional, can be removed)

```bash
# Start all services
docker compose up -d

# Run migrations
docker compose exec app php artisan migrate --force

# Create a user
docker compose exec app php artisan users:create

# Seed default ticket types
docker compose exec app php artisan db:seed --class=TicketTypeSeeder --force
```

## Documentation Site

The documentation is built with [Docusaurus](https://docusaurus.io/).

```bash
# Install dependencies
yarn

# Local development
yarn start

# Production build
yarn build
```
