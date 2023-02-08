# Terraform with GCP

## Content

- [Terraform with GCP](#terraform-with-gcp)
  - [Content](#content)
  - [Prerequisites](#prerequisites)
  - [Terraform Configuration with Google Provider Configuration](#terraform-configuration-with-google-provider-configuration)
    - [Managing Account](#managing-account)
    - [Example Terraform Code With Google Provider](#example-terraform-code-with-google-provider)
  - [Google Cloud Storage (GCS) Terraform Backend Setup](#google-cloud-storage-gcs-terraform-backend-setup)
  - [Initialise Backend](#initialise-backend)

## Prerequisites

- A valid GCP account.
  - Google service account having required permissions to resources that you are trying to manage using Terraform. Get it from the [Google Cloud IAM console][1].
- Some basic knowledge about Terraform configuration.

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

> Note: `${file("service-account.json")}` looks for the service account key in the current folder where you are running the terraform command.

### Managing Account

You can manage the service account in the following ways.

1. Enter the path of the service account file with the credentials key. For example,

    `credentials = "${file("/opt/terraform/service-account.json")}"`

2. Set a credential environment variable `GOOGLE_CLOUD_KEYFILE_JSON`. In this case, we don’t have to use credentials key in the provider definition. Terraform will automatically pick up the credential location from the environment variable. Example,

`export GOOGLE_CLOUD_KEYFILE_JSON="/opt/terraform/service-account.json"`

> Note: export will only set the environment variable in the current terminal. To set a permanent environment variable, you need to add it to the user/system profile.

### Example Terraform Code With Google Provider

```yaml
provider "google" {
  credentials = "${file("/opt/creds/service-account.json")}"
  project     = "devopscube-demo"
  region      = "us-central1"
}
resource "google_compute_instance" "ubuntu-xenial" {
   name = "devopscube-demo-instance"
   machine_type = "f1-micro"
   zone = "us-west1-a"
   boot_disk {
       auto_delete = false
      initialize_params {
      image = "ubuntu-1604-xenial-v20181023"
      size = "30"     
   }
}
network_interface {
   network = "default"
   access_config {}
}

metadata {
    foo = "bar"
}

metadata_startup_script = "echo demo > /demo.txt"

scheduling {
    preemptible = true
  }

service_account {
   scopes = ["cloud-platform"]
   }
}
```

> Note: Once you execute the init command, terraform will automatically download the Google backend plugin.

## Google Cloud Storage (GCS) Terraform Backend Setup

During every terraform run, terraform creates a state file for the executed plan. By default, it creates the state in the local file system. You can store this state in remote GCS backend.

Before getting started, you need to have the following.

1. GCS Bucket: A google storage bucket where you want to save the terraform state. You can create one from here.
2. Valid Google Service Account: Google service account with permissions to write to the storage bucket used by Terraform to save the states.

GCS backend configuration has the following key-value pairs.

1. Bucket: Google storage bucket name.
1. Prefix: Folders inside the bucket.
1. Credentials: Path to google service account file.

Backend configuration will look like this. You should have this backend configuration in your root terraform file.

```yaml
terraform {
  backend "gcs" {
    bucket      = "data-bucket-name"
    prefix      = "demo"
    credentials = "service-account.json"
  }
}
```

## Initialise Backend

You need to initialize the GCS backend for the first time using the init command. This would read all the backend configuration from the terraform block and initialize a state file in the bucket path.

`terraform init`

You can also pass the backend configuration in the runtime using a partial configuration.
The terraform block would have an empty declaration as shown below.

```yaml
terraform {
  backend "gcs" {}  
}
```

Now, you can pass the backend configurations with the init command as shown below.

```bash
terraform init \
    -backend-config="data-bucket-name" \
    -backend-config="prefix=demo" \
    -backend-config="credentials=service-account.json"
```

You can also pass the backend configuration as a file during runtime.

> Note: This is a perfect use case of using secrets with vault. You can store your backend configs in vault and retrieve it during terraform initialization. Covering vault integration in out of the scope of this article.

For example, create a file named backend.config and enter all the backend details as key-value pairs as shown below.

```yaml
bucket      = "data-bucket-name"
prefix      = "demo"
credentials = "service-account.json"
```

You can pass this file with the init command as follows.

`terraform init -backend-config=backend.config`

[1]:https://console.cloud.google.com/iam-admin/serviceaccounts