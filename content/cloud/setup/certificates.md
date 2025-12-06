---
title: Certificates
weight: 2
---

TLS certificates are required for machine-to-machine communication. A few certificates are necessary for the system to work properly, including:

* Root certificate
* gRPC certificate
* Redis certificate (Both server and client)
* UI certificate (optional)
* HTTPS certificate (optional)

The commands below require a `.conf` file for certificate generation, which can be found in the `/docker-compose/certs` folder. The certificates are for testing purposes only, so you can adjust the configurations, validity period, and passwords according to your needs.

Alternatively, run the `/docker-compose/certs/generate-certs.sh` script to generate the certificates.

## 1. Root Certificate

The root certificate forms the base of the certificate chain in LGDXRobot Cloud.

```bash
openssl req -newkey rsa:4096 -keyout rootCA.key -out rootCA.csr -config rootCA.conf -nodes 
openssl x509 -req -days 9999 -extfile rootCA.conf -extensions v3_ca -in rootCA.csr -signkey rootCA.key -out rootCA.crt
openssl pkcs12 -export -out rootCA.pfx -inkey rootCA.key -in rootCA.crt -passout pass:""
```

Next, install the root certificate in the operating system then trust the root certificate.

## 2. gRPC Certificate

The gRPC certificate is used for communication between the API and the robots via gRPC.

Ensure the [alt_names] section in the `grpc.conf` file is set to the IP address of the machine running the API.
{.alert .alert-info}

```bash
openssl req -newkey rsa:4096 -keyout grpc.key -out grpc.csr -config grpc.conf -nodes 
openssl x509 -req -in grpc.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out grpc.crt -days 9999 -sha256 -extfile grpc.conf -extensions req_ext
openssl pkcs12 -export -out grpc.pfx -inkey grpc.key -in grpc.crt -certfile rootCA.crt -passout pass:""
```

Next, copy the `grpc.pfx` to the base directory of the `LGDXRobotCloud.API` project.

## 3. Redis Certificate

Generate a certificate for the Redis server.

```bash
openssl req -newkey rsa:4096 -keyout redis_server.key -out redis_server.csr -config redis_server.conf -nodes 
openssl x509 -req -in redis_server.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out redis_server.crt -days 9999 -sha256 -extfile redis_server.conf -extensions req_ext
openssl pkcs12 -export -out redis_server.pfx -inkey redis_server.key -in redis_server.crt -certfile rootCA.crt -passout pass:""
```

Generate a certificate for the clients.

```bash
openssl req -newkey rsa:4096 -keyout redis_client.key -out redis_client.csr -config redis_client.conf -nodes 
openssl x509 -req -in redis_client.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out redis_client.crt -days 9999 -sha256 -extfile redis_client.conf -extensions req_ext
openssl pkcs12 -export -out redis_client.pfx -inkey redis_client.key -in redis_client.crt -certfile rootCA.crt -passout pass:""
```

Next, install the certificate (Only client certificate is required) in the operating system.

## 4. UI Certificate

The UI certificate is used for certificate-based authentication in the API. It can be omitted if the system is started in development mode.

```bash
openssl req -newkey rsa:4096 -keyout ui.key -out ui.csr -config ui.conf -nodes 
openssl x509 -req -in ui.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out ui.crt -days 9999 -sha256 -extfile ui.conf -extensions req_ext
openssl pkcs12 -export -out ui.pfx -inkey ui.key -in ui.crt -certfile rootCA.crt -passout pass:""
```

Next, install the certificate in the operating system.

## 5. HTTPS Certificate

The HTTPS certificate is used for HTTPS communication between the API, the UI, and the browser. It can be replaced with a .NET dev-certificate.

Ensure the [alt_names] section in the `app.conf` file is set to the IP address of the machine running the API.
{.alert .alert-info}

```bash
openssl req -newkey rsa:4096 -keyout app.key -out app.csr -config app.conf -nodes 
openssl x509 -req -in app.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out app.crt -days 9999 -sha256 -extfile app.conf -extensions req_ext
openssl pkcs12 -export -out app.pfx -inkey app.key -in app.crt -certfile rootCA.crt -passout pass:""
```

## Before the Next Steps

Make sure the following certificates are installed on the operating system and that the root certificate is trusted:

* Root certificate
* Redis certificate (client only)
* UI certificate

Then copy the `grpc.pfx` file to the base directory of the `LGDXRobotCloud.API` project.
