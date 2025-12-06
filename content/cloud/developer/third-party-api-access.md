---
title: Third-Party API Access
weight: 1
---

This tutorial describes how to gain access to the API using Postman.

## Authentication to the API

1. Create an LGDXRobot Cloud API Key and note the secret key.
2. In Postman, create a new request `https://localhost:5163/Identity/Auth/Login` and set the method to `POST`.
3. In the **Headers** tab, add a new key `X-API-Key` and set the value to the API Key.

![Screenshot of adding the X-API-Key header](../img/third-party/api-login-header.png)

4. In the **Body** tab, add a JSON object with the following properties:

```json
{
  "username": "<User name>",
  "password": "<Password>"
}
```

![Screenshot of adding the body](../img/third-party/api-login-body.png)

5. Click **Send**.
6. Note the `accessToken` and `refreshToken` in the response.

## Access the API

1. In Postman, create a new request `https://localhost:5163/Navigation/Realms` and set the method to `GET`.
2. In the **Headers** tab, add a new key `X-API-Key` and set the value to the API Key.
3. In the **Headers** tab, add a new key `Authorization` and set the value to `Bearer <accessToken>`.

![Screenshot of adding the headers](../img/third-party/api-call.png)

4. Click **Send**.
5. The first realm will be shown in the response.

## Refresh the Access Token

LGDXRobot Cloud allows refreshing the access token, which is useful for users in third-party UIs that do not require re-authentication. The refresh token can only be used once.

1. In Postman, create a new request `https://localhost:5163/Identity/Auth/Refresh` and set the method to `POST`.
2. In the **Headers** tab, add a new key `X-API-Key` and set the value to the API Key.
3. In the **Headers** tab, add a new key `Authorization` and set the value to `Bearer <accessToken>`.

![Screenshot of adding the headers](../img/third-party/api-refresh-header.png)

4. In the **Body** tab, add a JSON object with the following properties:

```json
{
  "refreshToken": "<refreshToken>"
}
```

![Screenshot of adding the body](../img/third-party/api-refresh-body.png)

5. Click **Send**.
6. The new `accessToken` and `refreshToken` will be shown in the response.
