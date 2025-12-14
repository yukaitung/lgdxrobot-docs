---
title: Administration - API Robot Certificates
weight: 154
---

This page manages all certificates for the robots. It displays the thumbprint and validity of each certificate, and provides functionality to renew certificates.

## Checking the Root Certificate

* Click the **Check Root Certificate** button at the top right.
* A new window will open with the certificate details.

## Renewing the Root Certificate

* Click the **View** button on the right of the certificate (may need to scroll right).
* Click **Renew Certificate**.
* The renewal process will start.

1. Begin

* **Revoke Certificate**: If this option is checked, the current certificate will be revoked after the renewal process is complete. Otherwise, the certificate will remain valid until the expiration date.
* Press **Next** to continue.

2. Download Certificates

* Press **Download** to download the Root Certificate, Robot Private Key, and Robot Public Key files.  
  The input fields allow to change the file names before downloading.
* Press **Next** after the files have been downloaded.

The system does not store the key pair files, but they can be regenerated if lost.
{.alert .alert-info}

3. Complete

* Press **Done** in the final step.
