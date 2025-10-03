---
title: Dependencies
weight: 3
---

## Software Dependencies

The commands below install dependencies using Docker.

### PostgreSQL

```bash
docker run --name postgres \
  -e POSTGRES_PASSWORD=<enter a password> \
  -e POSTGRES_USER=<enter a username> \
  -e POSTGRES_DB=LGDXRobotCloud \
  -v postgres-data:/var/lib/postgresql/data \
  -p 5432:5432 \
  -d postgres
```

### RabbitMQ

```bash
docker run --name rabbitmq \
  -p 5672:5672 \
  -p 15672:15672 -d \
  rabbitmq:4.0-management
```

### Redis
 
And example of `redis.conf` is located in the `/docker-compose/` folder.

```bash
docker run -d --name redis \
  -v <location to redis certificate>:/certs \
  -v <location to redis.conf>:/usr/local/etc/redis/redis.conf \
  -p 6379:6379 \
  redis \
  redis-server /usr/local/etc/redis/redis.conf
```

### SMTP Server

LGDXRobot Cloud relies on email for notifications, but no specific SMTP server is recommended for development. You can use the SMTP servers of free email providers, such as Gmail, Outlook, or iCloud. Alternatively, you can skip this setup, but you will not receive notifications.
