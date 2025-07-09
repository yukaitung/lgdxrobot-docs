---
title: Prerequisites
weight: 2
---

## Certificate

TLS certificates are required for machine-to-machine communication. A few certificates are necessary for the system to work properly, including: root certificate, gRPC certificate, UI certificate (optional), and HTTPS certificate (optional).

The commands below require a `.conf` file for certificate generation, which can be found in the `/docker-compose/certs` folder.

### Root Certificate

The root certificate forms the base of the certificate chain in LGDXRobot Cloud.

```bash
openssl req -newkey rsa:4096 -keyout rootCA.key -out rootCA.csr -config rootCA.conf -nodes 
openssl x509 -req -days 9999 -extfile rootCA.conf -extensions v3_ca -in rootCA.csr -signkey rootCA.key -out rootCA.crt
openssl pkcs12 -export -out rootCA.pfx -inkey rootCA.key -in rootCA.crt -passout pass:""
```

Next, trust the root certificate in the operating system.

### gRPC Certificate

The gRPC certificate is used for communication between the API and the robots via gRPC.

```bash
openssl req -newkey rsa:4096 -keyout grpc.key -out grpc.csr -config grpc.conf -nodes 
openssl x509 -req -in grpc.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out grpc.crt -days 9999 -sha256 -extfile grpc.conf -extensions req_ext
openssl pkcs12 -export -out grpc.pfx -inkey grpc.key -in grpc.crt -certfile rootCA.crt -passout pass:""
```

Next, copy the `grpc.pfx` to the base directory of the `LGDXRobotCloud.API` project.

### UI Certificate

The UI certificate is used for certificate-based authentication in the API. It can be omitted if the system is started in development mode.

```bash
openssl req -newkey rsa:4096 -keyout ui.key -out ui.csr -config ui.conf -nodes 
openssl x509 -req -in ui.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out ui.crt -days 9999 -sha256 -extfile ui.conf -extensions req_ext
openssl pkcs12 -export -out ui.pfx -inkey ui.key -in ui.crt -certfile rootCA.crt -passout pass:""
```

### HTTPS Certificate

The HTTPS certificate is used for HTTPS communication between the API, the UI, and the browser. It can be replaced with a .NET dev-certificate.

```bash
openssl req -newkey rsa:4096 -keyout app.key -out app.csr -config app.conf -nodes 
openssl x509 -req -in app.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out app.crt -days 9999 -sha256 -extfile app.conf -extensions req_ext
openssl pkcs12 -export -out app.pfx -inkey app.key -in app.crt -certfile rootCA.crt -passout pass:""
```

## Software Dependencies

The commands below install dependencies using Docker.

### PostgreSQL

```bash
docker run --name postgres -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=admin -e POSTGRES_DB=LGDXRobotCloud -v postgres-data:/var/lib/postgresql/data -p 5432:5432 -d postgres
```

### RabbitMQ

```bash
docker run --name rabbitmq -p 5672:5672 -p 15672:15672 -d rabbitmq:4.0-management
```

### SMTP Server

LGDXRobot Cloud relies on email for notifications, but there is no recommended SMTP server for development. You can use the SMTP server from free email providers, such as Gmail, Outlook, or iCloud.
