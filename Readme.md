Add GCP Account to Cloud One
To set up a new Cloud Account, you must deploy resources in your GCP account to provide access to Trend Micro Cloud One. You can deploy the Terraform template, which will create the required GCP permissions.

Requirements
Have a Cloud One account. Sign up for a free trial now if it's not already the case!
GCP CLI installed and configured.
Enable the following Google APIs:
Service	APIs & Services
BigQuery	BigQuery API
CloudAPI	API Keys API
CloudIAM	Cloud Resource Manager API
Identity and Access Management (IAM)
API Access Approval API
CloudKMS	Cloud Key Management Service (KMS) API
CloudVPC	Compute Engine API
CloudStorage	Cloud Storage API
ComputeEngine	Compute Engine API
CloudSQL	Cloud SQL Admin API
CloudLoadBalancing	Compute Engine API
CloudDNS	Cloud DNS API
Dataproc	Cloud Dataproc API
GKE	Kubernetes Engine API
CloudLogging	Cloud Logging API
PubSub	Cloud Pub/Sub API
ResourceManager	Cloud Resource Manager API
Setup IAM Permissions
To setup the IAM permission I've create a terraform template that you can use, it will create the policy, role and the attachment between them, first clone the repository to your machine and access the folder of this project, here the commands to deploy the permissions via terraform:

To install terraform, follow this Guide

First you need to provide in the terraform template (variables.tf file):

Project ID
GCP Region
Then you can execute the following:

cd IAM
terraform init
terraform plan -out=plan
terraform apply -auto-approve
