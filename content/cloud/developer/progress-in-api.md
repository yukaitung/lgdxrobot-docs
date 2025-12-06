---
title: Progress in API
weight: 3
---

This tutorial describes how to use the Next Token with a robot. This applies to both physical and simulated robots.

## Prerequisites

1. Create a RESTful API for receiving the Next Token by using the following Python script.

```python
from http.server import BaseHTTPRequestHandler, HTTPServer
import json

class Handler(BaseHTTPRequestHandler):
    def do_POST(self):
        length = int(self.headers['Content-Length'])
        body = self.rfile.read(length)
        data = json.loads(body)
        print(data)
        self.send_response(200)
        self.end_headers()
        self.wfile.write(b'OK')

HTTPServer(('', 8000), Handler).serve_forever()
```

2. Save the script as `server.py` and run it using `python server.py`.
3. Create an LGDXRobot Cloud API Key and note the secret key.
4. Create a trigger with the following properties:

Field | Value
--- | ---
Name | Test
URL | http://127.0.0.1:8000
Method | POST
{.table}

In the body, set the following properties:

Key | Value
--- | ---
TaskId | Task ID
RobotId | Robot ID
{.table}

![Screenshot of creating a trigger](../img/progress-in-api/trigger.png)

5. Create a new flow with two progress steps: **Loading** and **Moving**. The Proceed Condition for Loading is *API*, and the trigger is set to the trigger just created.

![Screenshot of creating a new flow](../img/progress-in-api/flow.png)

6. Connect a robot to LGDXRobot Cloud.

## Completing the Progress

1. Create a new task using the flow just created. The waypoints can be any waypoints in the realm.
2. The robot will not move because the current progress is **Loading**.
3. Note the Task ID, Robot ID, and Next Token from the terminal running the Python script.

![Screenshot of the python script](../img/progress-in-api/next-pyserver.png)

4. In Postman, create a new request `https://localhost:5163/Automation/AutoTasksNext/<Task ID>` and set the method to `POST`.
5. In the **Headers** tab, add a new key `X-API-Key` and set the value to the API Key.

![Screenshot of the request headers](../img/progress-in-api/next-header.png)

6. In the **Body** tab, add a JSON object with the following properties:

```json
{
  "robotId": "<Robot ID>",
  "nextToken": "<Next Token>"
}
```

![Screenshot of the request body](../img/progress-in-api/next-body.png)

7. Click **Send**.
8. The robot will move to the next waypoint.
