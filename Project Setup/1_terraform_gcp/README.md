## Setup for GCP and Terraform


### GCP setup

#### Initial Setup
For this project, GCP free version (upto EUR 300 credits) was used.

1. Created an account with my Google email ID
2. Setup of first project(DTC DE Course) if you haven't already and noted down the "Project ID"
3. Setup of service account & authentication for this project
4. Granted Viewer role to begin with
5. Downloaded service-account-keys (.json) for auth
6. Downloaded SDK for local setup
7. Set environment variable to point to the downloaded GCP keys:
   ```shell
   export GOOGLE_APPLICATION_CREDENTIALS="<path/to/your/service-account-authkeys>.json"
   
   # Refresh token/session, and verify authentication
   gcloud auth application-default login
   ```

#### Setup for Access:

1. IAM Roles for Service account
2. Navigated to the IAM section of IAM & Admin
3. Clicked the Edit principal icon for my service account
4. Added these roles in addition to Viewer : Storage Admin + Storage Object Admin + BigQuery Admin


#### Enabled these APIs for my project:

https://console.cloud.google.com/apis/library/iam.googleapis.com
https://console.cloud.google.com/apis/library/iamcredentials.googleapis.com


### Terraform setup

1. Installed Terraform for windows
2. Navigated to the terraform directory
3. Performed the following execution steps to create the GCP infrastructure
  ```shell
# Refresh service-account's auth-token for this session
gcloud auth application-default login

# Initialize state file (.tfstate)
terraform init

# Check changes to new infra plan
terraform plan -var="project=<your-gcp-project-id>"
```

```shell
# Create new infra
terraform apply -var="project=<your-gcp-project-id>"
```

```shell
# Delete infra after your work, to avoid costs on any running services
terraform destroy
```







   
