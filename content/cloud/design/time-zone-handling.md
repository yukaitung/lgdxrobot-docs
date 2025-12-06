---
title: Time Zone Handling
weight: 5
---

LGDXRobot Cloud was developed in a region that has summer time, and this page describes how it handles time zones. The system uses the UTC time zone, so third-party systems are responsible for converting the time zone. If the user accesses the system using the LGDXRobot Cloud UI, the time zone is automatically converted, provided that the user has set the correct time zone in the operating system.

## LGDXRobot Cloud UI Time Zone Handling

1. When the user accesses the login page, the system automatically detects the time zone using JavaScript.
2. The time zone is included in the user session when the user logs in.
3. The UI automatically converts the time zone when displaying times.

If the time zone is changed, the user will need to log out and log in again to see the updated time.
