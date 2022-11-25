# Conformity-AddAcount-GCP
Add Conformity GCP Account with gcloud cli and TF to Cloud One

To set up a new Cloud Account, you must deploy resources in your GCP account to provide access to Trend Micro Cloud One. You can deploy the Terraform template, which will create the required GCP permissions.

## Requirements

- Have a [Cloud One](https://www.trendmicro.com/cloudone) account. [Sign up for a free trial now](https://cloudone.trendmicro.com/register) if it's not already the case!
- GCP CLI [installed](https://cloud.google.com/sdk/docs/install) and [configured](https://cloud.google.com/sdk/docs/initializing).
- Enable the following Google APIs:

|Service|APIs & Services|
|---|---|
|BigQuery|BigQuery API|
|CloudAPI|API Keys API|
|CloudIAM|Cloud Resource Manager API<br>Identity and Access Management (IAM)<br>API Access Approval API|
|CloudKMS|Cloud Key Management Service (KMS) API|
|CloudVPC|Compute Engine API|
|CloudStorage|Cloud Storage API|
|ComputeEngine|Compute Engine API|
|CloudSQL|Cloud SQL Admin API|
|CloudLoadBalancing|Compute Engine API|
|CloudDNS|Cloud DNS API|
|Dataproc|Cloud Dataproc API|
|GKE|Kubernetes Engine API|
|CloudLogging|Cloud Logging API|
|PubSub|Cloud Pub/Sub API|
|ResourceManager|Cloud Resource Manager API|

## enable API through gcloud cli with: (Billing Account need to be enabled first!)
```
gcloud services enable bigquery.googleapis.com
gcloud services enable apikeys.googleapis.com
gcloud services enable cloudresourcemanager.googleapis.com
gcloud services enable iam.googleapis.com
gcloud services enable accessapproval.googleapis.com
gcloud services enable cloudkms.googleapis.com
gcloud services enable compute.googleapis.com
gcloud services enable storage.googleapis.com
gcloud services enable compute.googleapis.com
gcloud services enable sqladmin.googleapis.com
gcloud services enable compute.googleapis.com
gcloud services enable dns.googleapis.com
gcloud services enable dataproc.googleapis.com
gcloud services enable container.googleapis.com
gcloud services enable logging.googleapis.com
gcloud services enable pubsub.googleapis.com
gcloud services enable cloudresourcemanager.googleapis.com
```

You can use the gcp-api.sh script to enable the needed APIs all ad once 

## get the repo
```
git clone https://github.com/Robi1021/Conformity-AddAcount-GCP.git
```

## Setup IAM Permissions

To setup the IAM permission I've create a terraform template that you can use, it will create the policy, role and the attachment between them, first clone the repository to your machine and access the folder of this project, here the commands to deploy the permissions via terraform:

 To install terraform, follow this [Guide](https://learn.hashicorp.com/tutorials/terraform/install-cli#install-terraform)

 First you need to provide in the terraform template (variables.tf file or use the example `gcp.tfvars` file, these are the values that need to be provided::

- Project ID
- GCP Region

 Then you can execute the following:

   ```bash
   terraform init
   terraform plan -out=plan
   terraform apply -auto-approve
   terraform apply -var-file="gcp.tfvars` (In case you decided to use the `gcp.tfvars`)
   ```
