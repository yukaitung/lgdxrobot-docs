---
title: Configuation - Data
weight: 5
---

Update the corresponding `appsettings.json`.

For managing secrets securely, please refer to the [Official Documentation](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) on how to create and handle secrets in your environment.

## Secrets

```json
"ConnectionStrings": {
  "Default": "Host=postgres;Username=admin;Password=mysecretpassword;Database=LGDXRobotCloud;",
  "Activity": "Host=postgres;Username=admin;Password=mysecretpassword;Database=LGDXRobotCloudLogs;"
}
```

### `ConnectionStrings` Subkeys

| Key         | Description                                             |
|-------------|---------------------------------------------------------|
| Default     | The connection strings to default PostgreSQL database  |
| Activity    | The connection strings to activity logs PostgreSQL database |
{.table}
