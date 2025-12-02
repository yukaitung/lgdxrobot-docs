---
title: Architecture
weight: 2
---

LGDXRobot Cloud uses a three-tier architecture consisting of a UI front end (Presentation Layer), an API and Worker service (Application Layer), and a database (Data Layer). The connections between each component and the end user (User and Robot) vary depending on the use case.

![System Architecture](../img/architecture/arch.png)

## LGDXRobot Cloud Components

- **UI**: A web-based user interface built with .NET Blazor for managing the system. It also provides real-time capabilities to display robot status.
- **API**: A RESTful API that serves as the system’s logic layer. It also acts as a gRPC service for communication between the API and the robots.
- **Worker**: A background service responsible for running time-consuming tasks, including email notifications, third-party webhooks, and auditing.

## External Components

- **Database**: A PostgreSQL database used for storing the system’s data.
- **RabbitMQ**: A message broker that enables reliable communication between the API and the Worker.
- **Redis**: A fast in-memory data store for caching robot status. It also acts as a queue for updating robot and task status for the UI.
- **SMTP**: A mail service used for sending email notifications.
