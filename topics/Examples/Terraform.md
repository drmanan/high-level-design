# Terraform with GCP

## Content

- [Terraform with GCP](#terraform-with-gcp)
  - [Content](#content)
  - [Prerequisites](#prerequisites)
  - [Terraform Configuration with Google Provider Configuration](#terraform-configuration-with-google-provider-configuration)

## Prerequisites

- A valid GCP account.
  - Google service account having required permissions to resources that you are trying to manage using Terraform. Get it from the [Google Cloud IAM console][1].

## Terraform Configuration with Google Provider Configuration

Terraform google cloud provider configuration is a series for key-value pairs and contains four pairs.

1. **Credentials** Google service account file path.
2. **Project** Google project which you want to manage.
3. **Region** Google cloud region.
4. **Zone** Google cloud zone.

An example configuration is given below. With this configuration, you can connect to Google account in the central region on devopscube-demo project.

```yaml
provider "google" {
  credentials = "${file("service-account.json")}"
  project     = "devopscube-demo"
  region      = "us-central1"
  zone        = "us-central1-c"
}
```

> Note: ${file("service-account.json")} looks for the service account key in the current folder where you are running the terraform command.


[1]:https://console.cloud.google.com/iam-admin/serviceaccounts