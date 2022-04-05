## Setup for GCP and Terraform


## GCP setup
Initial Setup
For this project, GCP free version (upto EUR 300 credits) was used.

Created an account with my Google email ID
Setup of first project(DTC DE Course) if you haven't already and noted down the "Project ID" 
Setup of service account & authentication for this project
Granted Viewer role to begin with.
Downloaded service-account-keys (.json) for auth.
Downloaded SDK for local setup
Set environment variable to point to your downloaded GCP keys:
SET GOOGLE_APPLICATION_CREDENTIALS="<path/to/your/service-account-authkeys>.json"
### Refreshed token/session, and verify authentication
gcloud auth application-default login


Setup for Access:

IAM Roles for Service account
Navigated to the IAM section of IAM & Admin
Clicked the Edit principal icon for my service account.
Added these roles in addition to Viewer : Storage Admin + Storage Object Admin + BigQuery Admin


Enabled these APIs for my project:

https://console.cloud.google.com/apis/library/iam.googleapis.com
https://console.cloud.google.com/apis/library/iamcredentials.googleapis.com


## Terraform setup
Installed Terraform for windows
Navigated to the terraform directory
Performed the following steps to create your infrastructure

### Refresh service-account's auth-token for this session
gcloud auth application-default login

### Initialize state file (.tfstate)
terraform init

### Check changes to new infra plan
terraform plan -var="project=<your-gcp-project-id>"

### Create new infra
terraform apply -var="project=<your-gcp-project-id>"
   
