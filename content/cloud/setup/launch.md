---
title: Launch
weight: 4
---

## Create Database

You need to create the database and a first user.

```bash
cd LGDXRobotCloud.Data
dotnet ef database update
dotnet run --initialiseData "true"  --email "email@example.com" --fullName "Full Name" --userName "admin" --password "password"
```

| Parameter        | Example Value       | Description                 |
|------------------|---------------------|-----------------------------|
| --initialiseData  | true                | Whether to initialise data   |
| --email          | email@example.com   | User email address           |
| --fullName       | Full Name           | User’s full name             |
| --userName       | admin               | Username                    |
| --password       | password            | User password               |
{.table}

## Run

You can run the application using `dotnet run` in below projects:

* LGDXRobotCloud.API
* LGDXRobotCloud.UI
* LGDXRobotCloud.Worker