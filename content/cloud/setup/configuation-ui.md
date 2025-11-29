---
title: Configuation - UI
weight: 6
---

Update the corresponding `appsettings.json`.

For managing secrets securely, please refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create and handle secrets in your environment.

## Settings

```json
"Redis": {
  "ConnectionString": "localhost:6379",
  "CertificateSN": ""
},
"LGDXRobotCloudAPI" :{
  "Url" : "https://localhost:5163",
  "CertificateSN" : ""
}
```

### `LGDXRobotCloudAPI` Subkeys

| Key                          | Description                               |
|------------------------------|-------------------------------------------|
| Url                          | The URL of the LGDXRobotCloud API         |
| CertificateSN                | The serial number of the API certificate |
{.table}

To find `CertificateSN`, run the following command:

```bash
openssl x509 -in ui.crt -noout -serial
```

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