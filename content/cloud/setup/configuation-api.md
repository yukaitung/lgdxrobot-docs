---
title: Configuation - API
weight: 4
---

Update the corresponding `appsettings.json`.

For managing secrets securely, please refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create and handle secrets.

## Settings

```json
"LGDXRobotCloud": {
  "InternalCertificateThumbprint": "",
  "RootCertificateSN": "",
  "RobotCertificateValidDay": 365,
  "ApiMaxPageSize": 100
}
```

When setting endpoints, the port number for **gRPC** must be the lowest, and **HTTPS** must be the highest.

### `LGDXRobotCloud` Subkeys

| Key                           | Description                                                |
|-------------------------------|------------------------------------------------------------|
| InternalCertificateThumbprint | The thumbprint of the internal UI certificate              |
| RootCertificateSN             | The serial number of the root certificate                  |
| RobotCertificateValidDay      | The number of days that a robot certificate is valid       |
| ApiMaxPageSize                | The maximum number of items that can be returned in a page |
{.table}

To find `InternalCertificateThumbprint`, run the following command:

```bash
openssl x509 -in ui.crt -noout -fingerprint -sha1 | sed 's/://g'
```

To find `RootCertificateSN`, run the following command:

```bash
openssl x509 -in rootCA.crt -noout -serial
```

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
"Redis": {
  "ConnectionString": "redis:6379",
  "CertificateSN": ""
},
"LGDXRobotCloudSecret": {
  "LgdxUserJwtIssuer": "LGDXRobotCloudUsers", 
  "LgdxUserJwtSecret": "",
  "RobotClientsJwtIssuer": "LGDXRobotCloudobotClients", 
  "RobotClientsJwtSecret": "" 
}
```

### `ConnectionStrings` Subkeys

| Key         | Description                                                 |
|-------------|-------------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database       |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}

### `LGDXRobotCloudSecret` Subkeys

| Key                   | Description                                                  |
|------------------------|--------------------------------------------------------------|
| LgdxUserJwtIssuer      | The issuer of the JWT token for the users                   |
| LgdxUserJwtSecret      | The secret of the JWT token for the users (min 32 chars)    |
| RobotClientsJwtIssuer  | The issuer of the JWT token for the robot clients           |
| RobotClientsJwtSecret  | The secret of the JWT token for the robot clients (min 32 chars) |
{.table}

### `RabbitMq` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server      |
| VirtualHost | The virtual host of the RabbitMQ server                 |
| Username    | The username for the RabbitMQ server                    |
| Password    | The password for the RabbitMQ server                    |
| Port        | The port number of the RabbitMQ server                  |
{.table}

### `Redis` Subkeys

| Key              | Description                                                        |
|------------------|--------------------------------------------------------------------|
| ConnectionString | The host name or IP address of the Redis server (With port number) |
| CertificateSN    | The serial number of the Redis certificate                         |
{.table}

To find `CertificateSN`, run the following command:

```bash
openssl x509 -in redis_client.crt -noout -serial
```
