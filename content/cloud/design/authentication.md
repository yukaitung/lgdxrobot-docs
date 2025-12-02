---
title: Authentication
weight: 3
---

Security is important to LGDXRobot Cloud. Since the API contains nearly all system logic, authentication is required for all access. The authentication method varies depending on the component.

![System Authentication Diagram](../img/authentication/auth.png)

## Authentication Methods

* **UI**: Although the UI is an internal component, a certificate is required to access the API. The API validates both the certificate and its thumbprint to ensure that only the correct certificate is used.
* **User**: Users authenticate with a password and an optional 2FA token. Once authenticated, the API issues a JWT token for accessing protected resources. The JWT token is stored securely within the UI and is not accessible from the browser.
* **Robot**: Robots authenticate using certificates. The system validates both the certificate and its thumbprint. When renewing certificates, the system can optionally allow the previous certificate to remain valid during the transition. If validation is successful, the API issues a JWT token for gPRC communication. In addition, the system can optionally validate the hardware’s serial number to ensure that the certificate is not being reused on unauthorised devices.
* **Third-party**: Third-party systems must provide an API key when sending requests to the API. They must also authenticate using the same process as users to obtain a JWT token. However, the `Automation/AutoTasksNext` endpoint does not require a JWT token.
