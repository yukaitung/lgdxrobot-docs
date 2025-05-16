---
title: Configuation
weight: 3
---

Below are the configurations for the API, the UI, and the Worker. Most of the configuations are setting the connection to other services, so you need the creditials of the services below.

* PostgreSQL
* RabbitMQ
* SFTP

For the screts, refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create the secrets.

To obtain the Thumbprint

```bash
openssl x509 -in /path/to/certificate.crt -noout -fingerprint -sha1 | sed 's/://g'
```

To obtain the serial number

```bash
openssl x509 -in /path/to/certificate.crt -noout -serial
```

## 1. LGDXRobotCloud.API

### 1.1 appsettings.json

```json
"Kestrel": {
  "Endpoints": {
    "gRPC": {
      "Url": "https://*:5162",
      "Protocols": "Http2",
      "Certificate": {
        "Path": "grpc.pfx"
      }
    },
    "Internal": {
      "Url": "https://*:5163",
      "Protocols": "Http1AndHttp2"
    },
    "Https": {
      "Url": "https://*:5164",
      "Protocols": "Http1AndHttp2"
    }
  }
},
"LGDXRobotCloud": {
  "InternalCertificateThumbprint": "",
  "RootCertificateSN": "",
  "RobotCertificateValidDay": 365,
  "ApiMaxPageSize": 100
}
```

There are 3 endpoints for the API, `gRPC` for robots, `Internal` for internal UI, and `Https` for external web services. The port number for `gRPC` must be lowest and `Https` must be highest. Copy `grpc.pfx` to base of `LGDXRobotCloud.API` project.

#### `LGDXRobotCloud` Subkeys

| Key                         | Description                                              |
|----------------------------|----------------------------------------------------------|
| InternalCertificateThumbprint | The thumbprint of the internal UI certificate             |
| RootCertificateSN             | The serial number of the root certificate                |
| RobotCertificateValidDay     | The number of days that a robot certificate is valid     |
| ApiMaxPageSize               | The maximum number of items that can be returned in a page |
{.table}


### 1.2 Secrets

```json
{
  "PGSQLConnectionString": "Host=localhost;Username=admin;Password=secret;Database=LGDX", 
  "RabbitMq": {
    "Host": "localhost",
    "VirtualHost": "/",
    "Username": "username",
    "Password": "secret"
  },
  "LGDXRobotCloudSecret": {
    "LgdxUserJwtIssuer": "LGDXRobotCloudUsers",
    "LgdxUserJwtSecret": "secret with at least 32 characters", 
    "RobotClientsJwtIssuer": "LGDXRobotCloudobotClients", 
    "RobotClientsJwtSecret": "secret with at least 32 characters"
  }
}
```

#### Top-Level Keys

| Key                    | Description                                           |
|------------------------|-------------------------------------------------------|
| PGSQLConnectionString  | The connection string to the PostgreSQL database     |
| RabbitMq               | Settings for the RabbitMQ server                     |
| LGDXRobotCloudSecret   | JWT settings for users and robot clients             |
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

---

## 2 LGDXRobotCloud.Data

### 2.1 Secrets

```json
{
  "PGSQLConnectionString": "Host=localhost;Username=admin;Password=secret;Database=LGDXRobotCloud" 
}
```

#### Top-Level Keys

| Key                    | Description                                           |
|------------------------|-------------------------------------------------------|
| PGSQLConnectionString  | The connection string to the PostgreSQL database     |
{.table}

---

## 3 LGDXRobotCloud.UI

### 3.1 appsettings.json

```json
{
  "LGDXRobotCloudApiUrl": "https://localhost:5163", 
  "LGDXRobotCloudAPICertificateSN": ""
}
```

#### Top-Level Keys

| Key                          | Description                               |
|------------------------------|-------------------------------------------|
| LGDXRobotCloudApiUrl         | The URL of the LGDXRobotCloud API         |
| LGDXRobotCloudAPICertificateSN | The serial number of the API certificate |
{.table}

### 3.2 secrets

```json
{
  "RabbitMq": {
    "Host": "localhost",
    "VirtualHost": "/", 
    "Username": "username",
    "Password": "secret" 
  }
}
```

#### `RabbitMq` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Host        | The host name or IP address of the RabbitMQ server     |
| VirtualHost | The virtual host of the RabbitMQ server                |
| Username    | The username for the RabbitMQ server                   |
| Password    | The password for the RabbitMQ server                   |
{.table}

---

## 4 LGDXRobotCloud.Worker

### 4.1 appsettings.json

```json
"EmailLinks": { 
  "AccessUrl": "https://localhost:5103/",
  "PasswordResetPath": "ResetPassword" 
}
```

#### `EmailLinks` Configuration

| Key               | Description                                              |
|-------------------|----------------------------------------------------------|
| AccessUrl         | The URL of the LGDXRobotCloud UI                         |
| PasswordResetPath | The path to the password reset page in the LGDXRobotCloud UI |
{.table}

### 4.2 secrets

```json
{
  "PGSQLConnectionString": "Host=localhost;Username=admin;Password=secret;Database=LGDXRobotCloud", 
  "RabbitMq": {
    "Host": "localhost", 
    "VirtualHost": "/",
    "Username": "username", 
    "Password": "secret" 
  },
  "Email": {
    "FromName": "From name", 
    "FromAddress": "email address", 
    "Host": "SFTP server",
    "Port": 587, 
    "Username": "SFTP username",
    "Password": "SFTP password", 
  }
}
```

#### Top-Level Configuration

| Key                   | Description                                   |
|-----------------------|-----------------------------------------------|
| PGSQLConnectionString | The connection string to the PostgreSQL database |
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
| Host        | The host name or IP address of the SFTP server  |
| Port        | The port number of the SFTP server               |
| Username    | The username for the SFTP server                  |
| Password    | The password for the SFTP server                  |
{.table}
