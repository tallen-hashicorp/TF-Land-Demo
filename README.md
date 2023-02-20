# Terraform: Collaborative Infrastructure as Code
**[https://play.instruqt.com/hashicorp/tracks/terraform-collaborative-iac](https://play.instruqt.com/hashicorp/tracks/terraform-collaborative-iac)**

From Terraform OSS to Terraform Cloud - Transforming Our Infrastructure Workflow

In this demo we will introduce you to the main benefits of using Terraform over traditional deployment workflows.

* Introduction to traditional infrastructure deployment workflows
* Introduction to Terraform Open Source to solve some of the primary pain points of traditional workflows
* Introduction to Terraform Cloud/Enterprise and collaboration, security, VCS integration, etc...
* Going farther with module infrastructure
* Introduction to Governance and Policy-As-Code

# Links
* **[Instruqt Track](https://play.instruqt.com/hashicorp/tracks/terraform-collaborative-iac)**
* [TFC Cloud](https://app.terraform.io/app/tallen-playground/workspaces)

---
# Before running the instruqt track
* Create a new workspace in org in TFC
* **OPTIONL** Create a API Token, this can be found in [User Setting/Tokens](https://app.terraform.io/app/settings/tokens)
    * This is created for you

# DO THIS STEP BEFORE STARTING THE DEMO!
Running the following script provides the Instruqt track your TFC organization and API token. **Note: use the org name not id**
```bash
~/setup/scripts/tfc-setup.sh
```
Note that when you paste the token, it will not be displayed; don't paste it twice.

---
## Infrastructure-as-Code (IaC) Primer
```bash
cd /root/gitclones/hashicups-application
terraform init
terraform plan
terraform apply
```

**Outputs**
```
environment = "not-defined"
output = <<EOT

frontend: ssh -i ~/awskey.pem ubuntu@35.162.168.45
public-api: ssh -i ~/awskey.pem ubuntu@52.11.151.17
product-api: ssh -i ~/awskey.pem ubuntu@18.236.135.207
postgres: ssh -i ~/awskey.pem ubuntu@35.165.155.250

Takes a few mins to install packages:
http://35.162.168.45
```