---
title: Prerequisites
weight: 2
---

To run LGDXRobot Cloud, you'll need the following software:

- [.NET SDK](https://dotnet.microsoft.com/en-us/download)
- PostgreSQL
- RabbitMQ
- SMTP server (for sending emails)

PostgreSQL and RabbitMQ, can be easily set up using Docker.

### PostgreSQL

You can start a PostgreSQL container with a database named `LGDXRobotCloud` using:

```bash
docker run --name postgres -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=admin -e POSTGRES_DB=LGDXRobotCloud -v postgres-data:/var/lib/postgresql/data -p 5432:5432 -d postgres
```

To run RabbitMQ with the management interface:

```bash
docker run --name rabbitmq -p 5672:5672 -p 15672:15672 -d rabbitmq:4.0-management
```

An SMTP server is required for email functionality. You can either:

* Use an existing SMTP service that supports TLS (e.g., Gmail, Outlook) (Recommend)
* Host your own SMTP server using Docker or other tools

## Certificate

TLS certificates are required for secure communication between the cloud, robots, and UI.

### Root Certificate

Create the root certificate:

```bash
openssl genrsa -out rootCA.key 4096
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 3650 -out rootCA.crt
```

Convert it to .pfx format and add it to your system's trusted certificates:

```bash
openssl pkcs12 -export -out rootCA.pfx -inkey rootCA.key -in rootCA.crt
```

### Certificate For Robots Connection (gRPC)

Create a config file named `grpc.conf`. Replace `192.168.1.123` with your actual server IP:

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

Generate the private key and CSR:

```bash
openssl genrsa -out grpc.key 2048
openssl req -new -key grpc.key -out grpc.csr -config grpc.conf
```

Create and export the certificate:

```bash
openssl x509 -req -in grpc.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out grpc.crt -days 365 -sha256 -extfile grpc.conf -extensions req_ext
openssl pkcs12 -export -out grpc.pfx -inkey grpc.key -in grpc.crt -certfile rootCA.crt
```

### Certificate For UI (Optional)

This certificate is optional and only required for internal HTTPS between the UI and API.

Create a file called `ui.conf`:

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

Generate the private key and CSR:

```bash
openssl genrsa -out ui.key 2048
openssl req -new -key ui.key -out ui.csr -config ui.onf
```

Create and export the certificate:

```bash
openssl x509 -req -in ui.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out ui.crt -days 365 -sha256 -extfile ui.conf -extensions req_ext
openssl pkcs12 -export -out ui.pfx -inkey ui.key -in ui.crt -certfile rootCA.crt
```

Add `ui.pfx` to your system’s trusted certificate store if needed.