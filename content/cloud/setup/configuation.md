---
title: Configuation
weight: 3
---

Below are the configurations for LGDXRobot Cloud. Update the corresponding `appsettings.json`.

For managing secrets securely, please refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create and handle secrets in your environment.

Example configurations are provided in the `/docker-compose` folder.

## 1. LGDXRobotCloud.API

### Settings

When setting endpoints, the port number for **gRPC** must be the lowest, and **HTTPS** must be the highest.

#### `LGDXRobotCloud` Subkeys

| Key                         | Description                                              |
|----------------------------|----------------------------------------------------------|
| InternalCertificateThumbprint | The thumbprint of the internal UI certificate             |
| RootCertificateSN             | The serial number of the root certificate                |
| RobotCertificateValidDay     | The number of days that a robot certificate is valid     |
| ApiMaxPageSize               | The maximum number of items that can be returned in a page |
{.table}

To find `InternalCertificateThumbprint`, run the following command:

```bash
openssl x509 -in ui.crt -noout -fingerprint -sha1 | sed 's/://g'
```

To find `RootCertificateSN`, run the following command:

```bash
openssl x509 -in rootCA.crt -noout -serial
```

### Secrets

#### `ConnectionStrings` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database  |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}

#### `RabbitMq` Subkeys (Optional)

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The virtual host of the RabbitMQ server                |
| Activity    | The virtual host of the RabbitMQ server                |
{.table}

#### `RabbitMq` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server     |
| VirtualHost | The virtual host of the RabbitMQ server                |
| Username    | The username for the RabbitMQ server                   |
| Password    | The password for the RabbitMQ server                   |
{.table}

#### `LGDXRobotCloudSecret` Subkeys

| Key                   | Description                                                  |
|------------------------|--------------------------------------------------------------|
| LgdxUserJwtIssuer      | The issuer of the JWT token for the users                   |
| LgdxUserJwtSecret      | The secret of the JWT token for the users (min 32 chars)    |
| RobotClientsJwtIssuer  | The issuer of the JWT token for the robot clients           |
| RobotClientsJwtSecret  | The secret of the JWT token for the robot clients (min 32 chars) |
{.table}

## 2. LGDXRobotCloud.Data

### Secrets

#### `ConnectionStrings` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database  |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}

## 3. LGDXRobotCloud.UI

### Settings

#### `LGDXRobotCloudAPI` Subkeys

| Key                          | Description                               |
|------------------------------|-------------------------------------------|
| Url                          | The URL of the LGDXRobotCloud API         |
| CertificateSN                | The serial number of the API certificate |
{.table}

To find `CertificateSN`, run the following command:

```bash
openssl x509 -in ui.crt -noout -serial
```

### Secrets

#### `RabbitMq` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server     |
| VirtualHost | The virtual host of the RabbitMQ server                |
| Username    | The username for the RabbitMQ server                   |
| Password    | The password for the RabbitMQ server                   |
{.table}

## 4. LGDXRobotCloud.Worker

### Settings

#### `EmailLinks` Configuration

| Key               | Description                                              |
|-------------------|----------------------------------------------------------|
| AccessUrl         | The URL of the LGDXRobotCloud UI                         |
| PasswordResetPath | The path to the password reset page in the LGDXRobotCloud UI |
{.table}

### Secrets

#### `ConnectionStrings` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database  |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}

#### `RabbitMq` Subkeys

| Key         | Description                                           |
|-------------|-------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server   |
| VirtualHost | The virtual host of the RabbitMQ server              |
| Username    | The username for the RabbitMQ server                 |
| Password    | The password for the RabbitMQ server                 |
{.table}

#### `Email` Subkeys

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
