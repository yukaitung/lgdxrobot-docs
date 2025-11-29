---
title: Configuation - Worker
weight: 7
---

Update the corresponding `appsettings.json`.

For managing secrets securely, please refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create and handle secrets in your environment.

## Settings

```json
"EmailLinks": {
  "AccessUrl": "https://localhost:5103/",
  "PasswordResetPath": "ResetPassword"
}
```

### `EmailLinks` Configuration

| Key               | Description                                              |
|-------------------|----------------------------------------------------------|
| AccessUrl         | The URL of the LGDXRobotCloud UI                         |
| PasswordResetPath | The path to the password reset page in the LGDXRobotCloud UI |
{.table}

## Secrets

```json
"ConnectionStrings": {
  "Default": "Host=postgres;Username=admin;Password=mysecretpassword;Database=LGDXRobotCloud;",
  "Activity": "Host=postgres;Username=admin;Password=mysecretpassword;Database=LGDXRobotCloudLogs;"
},
"RabbitMq": {
  "HostName": "rabbitmq",
  "Port": 5672,
  "UserName": "guest",
  "Password": "guest",
  "VirtualHost": "/"
},
"Email": {
  "FromName": "",
  "FromAddress": "",
  "Host": "",
  "Port": 25, 
  "Username": "", 
  "Password": "",
  "SecureSocketOptions": 1
}
```

### `ConnectionStrings` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database  |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}

### `RabbitMq` Subkeys

| Key         | Description                                           |
|-------------|-------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server   |
| VirtualHost | The virtual host of the RabbitMQ server              |
| Username    | The username for the RabbitMQ server                 |
| Password    | The password for the RabbitMQ server                 |
{.table}

### `Email` Subkeys

| Key         | Description                                      |
|-------------|--------------------------------------------------|
| FromName    | The name of the sender                           |
| FromAddress | The email address of the sender                  |
| Host        | The host name or IP address of the SMTP server  |
| Port        | The port number of the SMTP server               |
| Username    | The username for the SMTP server                  |
| Password    | The password for the SMTP server                  |
|SecureSocketOptions|[Secure connect setting for the SMTP server](https://mimekit.net/docs/html/T_MailKit_Security_SecureSocketOptions.htm) |
{.table}
