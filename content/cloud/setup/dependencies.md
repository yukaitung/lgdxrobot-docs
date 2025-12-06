---
title: Dependencies
weight: 3
---

The dependencies can be installed using Docker.

## 1. PostgreSQL

```bash
docker run --name postgres \
  -e POSTGRES_PASSWORD=<enter a password> \
  -e POSTGRES_USER=<enter a username> \
  -e POSTGRES_DB=LGDXRobotCloud \
  -v postgres-data:/var/lib/postgresql \
  -p 5432:5432 \
  -d postgres:18
```

## 2. RabbitMQ

```bash
docker run --name rabbitmq \
  -p 5672:5672 \
  -p 15672:15672 -d \
  rabbitmq:4
```

Or with management UI:

```bash
docker run --name rabbitmq \
  -p 5672:5672 \
  -p 15672:15672 -d \
  rabbitmq:4-management
```

## 3. Redis

The Redis server requires a certificate. Copy the following certificates to a suitable location:

* Root certificate
* Redis certificate (server `.crt` and `.key`)

Then copy `/docker-compose/redis.conf` to a suitable location.

```bash
docker run -d --name redis \
  -v <location to redis certificate>:/certs \
  -v <location to redis.conf>:/usr/local/etc/redis/redis.conf \
  -p 6379:6379 \
  redis:8 \
  redis-server /usr/local/etc/redis/redis.conf
```

## 4. SMTP Server

LGDXRobot Cloud relies on email for notifications, but no specific SMTP server is recommended for development. You can use the SMTP servers of free email providers, such as Gmail, Outlook, or iCloud. Alternatively, you can skip this setup, but you will not receive notifications.
