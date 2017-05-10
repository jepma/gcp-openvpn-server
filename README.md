# OpenVPN Server - GCP

This file holds a simple configuration of a openvpn-server, at the Google Cloud Platform.

## Todo

1. Run automated configuration script
2. Add SSH-keys based upon terraform configuration
3. Allow SSH traffic only via console and connected VPN devices.

## Configure service-account

First we have to create the tfvars file that holds the service-account. It is important to **NOT** put this in GIT. This contains critical information that should **NOT** be shared.

```tfvars
env_name = "open-vpn"
region = "europe-west1"
zones = ["europe-west1-d", "europe-west1-b", "europe-west1-c"]
project = "marcel-vpn"
vpn_host_name = "VPN.YOUROSTHERE.COM"
service_account_key = <<SERVICE_ACCOUNT_KEY
{
  "type": "service_account",
  "project_id": "my-vpn",
  "private_key_id": "e0c40d4e5a3aad67690d86983fd5e36eb7b9bc8e",
  "private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQCb+a9bJrjhNtAQ\ntMb2xfnm0AqRhzegCV9H10/vd0Bww8yOj4Bx65eDXfuoq/77yasiUmwspeIeBZv7\n2VeojMCOhtER3VrzlnNYeYJqzUgj/VqT6Po4cAtEycA54kAErP\nwZ3w3hu4yvoKi5d911/k5g==\n-----END PRIVATE KEY-----\n",
  "client_email": "step-3@my-vpn.iam.gserviceaccount.com",
  "client_id": "100000000000000000000",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://accounts.google.com/o/oauth2/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/step-3%40my-vpn.iam.gserviceaccount.com"
}
SERVICE_ACCOUNT_KEY
```

## Install

You can install this openvpn server by running `terraform apply`.

```bash
$ terraform apply
```
