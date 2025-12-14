---
title: Launch
weight: 8
---

## Libraries for LGDXRobotCloud.UI

`LGDXRobotCloud.UI` requires several JavaScript libraries that can be managed using LibMan. Install the LibMan CLI and run the following command:

```bash
cd LGDXRobotCloud.UI
libman restore
```

## Create First User

`LGDXRobotCloud.Data` completes the database migration and creates the first user.

```bash
cd LGDXRobotCloud.Data
dotnet run --initialiseData "true" \
  --email "email@example.com" \
  --fullName "Full Name" \
  --userName "admin" \
  --password "password"
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

Run the application using `dotnet run` in the following projects:

* LGDXRobotCloud.API
* LGDXRobotCloud.UI
* LGDXRobotCloud.Worker

Alternatively, open the project with Visual Studio Code, switch to the **Run and Debug** tab, and choose running all projects or run a single project individually.

To access the frontend, visit [https://localhost:5103/Login](https://localhost:5103/Login). For the backend Scalar (an alternative to Swagger UI), visit [https://localhost:5163/scalar/](https://localhost:5163/scalar/). If the backend requests a certificate, choose **Not** to send the certificate.
