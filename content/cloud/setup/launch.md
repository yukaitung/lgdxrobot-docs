---
title: Launch
weight: 4
---

## Create First User

`LGDXRobotCloud.Data` completes the database migration and creates the first user.

```bash
cd LGDXRobotCloud.Data
dotnet run --initialiseData "true" --email "email@example.com" --fullName "Full Name" --userName "admin" --password "password"
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

You can run the application using `dotnet run` in the following projects:

* LGDXRobotCloud.API
* LGDXRobotCloud.UI
* LGDXRobotCloud.Worker

Alternatively, you can open the project with Visual Studio Code, switch to the **Run and Debug** tab, where you can choose to run all projects or run a single project individually.