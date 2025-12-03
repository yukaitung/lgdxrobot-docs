---
title: Architecture
weight: 2
---

LGDXRobot Cloud uses a three-tier architecture consisting of a UI front end (Presentation Layer), an API and Worker service (Application Layer), and a database (Data Layer). The connections between each component and the end user (User and Robot) vary depending on the use case.

![System Architecture](../img/architecture/arch.png)

## Connections

* **UI and third-party**: RESTful API calls
* **Robot**: gRPC, using streaming for real-time communication

## LGDXRobot Cloud Components

* **UI**: A web-based user interface built with .NET Blazor for managing the system. It also provides real-time capabilities to display robot status.
* **API**: A RESTful API built with ASP.NET Web API that serves as the system’s logic layer. It also acts as a gRPC service for communication between the API and the robots.
* **Worker**: A background service responsible for running time-consuming tasks, including email notifications, third-party webhooks, and auditing.

## External Components

* **Database**: A PostgreSQL database used for storing the system’s data.
* **RabbitMQ**: A message broker is used to send background task commands from the API to the Worker service in a reliable manner.
* **Redis**: A in-memory data store for caching robot status. It also acts as a queue for updating robot and task status for the UI.
* **SMTP**: A mail service used for sending email notifications.
