---
title: Prerequest
weight: 2
---

## Software

Install .Net

This application requires PostgreSQL, RabbitMQ and a SMTP server, you can install them using Docker. 

For the PostgreSQL, you can create it with a table called `LGDXRobotCloud` using the following command:

```bash
docker run --name postgres -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=admin -e POSTGRES_DB=LGDXRobotCloud -v postgres-data:/var/lib/postgresql/data -p 5432:5432 -d postgres
```

For RabbitMQ, you can use the following command:

```bash
docker run --name rabbitmq -p 5672:5672 -p 15672:15672 -d rabbitmq:4.0-management
```

You will need a SMTP server to sending emails. You can either use a free email service that have SMTP support, or you can build a SMTP server.

## Certificate

There are some certificates require in the setup.

### Root Certificate

Creating the private key for the root certificate:

```bash
openssl genrsa -out rootCA.key 4096
```

Creating the certificate:

```bash
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 3650 -out rootCA.crt
```

Convert the certificate to a pfx file, then add the certificate to trust certificate for the operating system.

```bash
openssl pkcs12 -export -out rootCA.pfx -inkey rootCA.key -in rootCA.crt
```

### Certificate For Robots Connection (gRPC)

The connection for robots requires certificate, so we need to create a certificate for grpc.

Create a config file `grpc.conf`, you can change the 192.168.1.123 to suitable IP address.

```
[req]
default_bits  = 2048
distinguished_name = req_distinguished_name
req_extensions = req_ext
x509_extensions = v3_req
prompt = no

[req_distinguished_name]
commonName = 192.168.1.123

[req_ext]
subjectAltName = @alt_names

[v3_req]
subjectAltName = @alt_names

[alt_names]
IP.1 = 127.0.0.1
IP.2 = 192.168.1.123
DNS.1 = localhost
```

Create a private key

```bash
openssl genrsa -out grpc.key 2048
```

Create a Certificate Signing Request file Using the Config

```bash
openssl req -new -key grpc.key -out grpc.csr -config grpc.conf
```

Then create a certificate using the CSR

```bash
openssl x509 -req -in grpc.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out grpc.crt -days 365 -sha256 -extfile grpc.conf -extensions req_ext
```

Convert it to .pfx, it is required for the configation

```bash
openssl pkcs12 -export -out grpc.pfx -inkey grpc.key -in grpc.crt -certfile rootCA.crt
```

### Certificate For UI (Optional)

Certificate can be used for internal connection between UI and API, however it is optional in development environment.

Create a config file `ui.conf`, you can change the ui.local to suitable name.

```
[req]
default_bits       = 2048
distinguished_name = req_distinguished_name
req_extensions     = req_ext
prompt             = no

[req_distinguished_name]
commonName         = ui.local

[req_ext]
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
```

Create a private key

```bash
openssl genrsa -out ui.key 2048
```

create a Certificate Signing Request file using the config

```bash
openssl req -new -key ui.key -out ui.csr -config ui.onf
```

Then create a certificate using the CSR

```bash
openssl x509 -req -in ui.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out ui.crt -days 365 -sha256 -extfile ui.conf -extensions req_ext
```

Then convert it to .pfx, and add the certificate to trust certificate

```bash
openssl pkcs12 -export -out ui.pfx -inkey ui.key -in ui.crt -certfile rootCA.crt
```
