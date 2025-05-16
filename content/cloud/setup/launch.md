---
title: Launch
weight: 4
---

## Create Database

You need to create the database and a first user.

```bash
cd LGDXRobotCloud.Data
dotnet ef database update && dotnet run --initialiseData "true"  --email "email@example.com" --fullName "Full Name" --userName "admin" --password "password"
```

## Run

You can run the application using `dotnet run` in below projects:

* LGDXRobotCloud.API
* LGDXRobotCloud.UI
* LGDXRobotCloud.Worker

## Extra Configuration

A map is required for the application to work, you should generate a map in ROS2 Nav2 stack.

1. Go to Navigation -> Realms and select "View" for "First Realm"
2. Convert the map from PGM to PNG, then upload the image
3. Update Resolution, Origin X, Origin Y, Origin Rotation
4. Restart LGDXRobotCloud.UI
