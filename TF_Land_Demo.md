# TF Land Demo Script

### Demo Artifacts:
* [Slides](https://drive.google.com/file/d/1YDpMHQSOWcbI0nWHT-5PND4kqXh1DDOI/view?usp=sharing)
* [Github Repository ](https://github.com/hashicorp/field-demos-terraform-land-team-Apollo-11)
* [Github Assets Repository](https://github.com/hashicorp/field-demos-terraform-land-team-Apollo-11-assets)
* [Instruqt Track](https://play.instruqt.com/hashicorp/tracks/terraform-collaborative-iac)
* [TFC](https://app.terraform.io/app/tallen-playground/workspaces)

The following Instruqt track is an introduction to Terraform over traditional deployment methods. The track is broken out into the following challenges.
1. Introduction to traditional infrastructure deployment workflows
2. Introduction to Terraform Open Source to solve some of the primary pain points of traditional workflows
3. Introduction to Terraform Cloud/Enterprise and collaboration, security, VCS integration, etc...
4. Going farther with modular infrastructure
5. Introduction to Governance and Policy-As-Code

**We strongly recommend that you start the track and then run the ~/setup/scripts/tfc-setup.sh script to give the track your TFC organization and API token BEFORE you start showing the demo.** While the check scripts expect that script to be run during challenge 2, it is better to run at the very beginning so that you don't have to show this step to the customer. This script used to be described at the end of the second challenge's assignment, but it is now in an extra note screen for the first challenge so that it does not have to be shown to customers during a demo.

We also recommend that you launch the GitLab server in a separate tab and login to it before you start showing the demo.  You should also have a browser tab opened to your organization in TFC open with the filter set to "hashicups" since the demo will eventually create 4 hashicups workspaces.

You might also want to get rid of some pesky popups that appear in the VS Code Editor before starting the demo for real.


# Setup Demo
* Create a new workspace in org in TFC
* **OPTIONL** Create a API Token, this can be found in [User Setting/Tokens](https://app.terraform.io/app/settings/tokens)
    * This ca be created for you during `~/setup/scripts/tfc-setup.sh`
* Start [Instruqt Track](https://play.instruqt.com/hashicorp/tracks/terraform-collaborative-iac)

## Tabs
* Instruqt
* GitLab
* TFC

---
# Demo

First track simply run `~/setup/scripts/tfc-setup.sh` and click **check**

## Demo Starts Here

* **Slides**
* Show Hashicorp Arch Slide
    * Simple 3 teir app with 3 webservers, 4 databases and networking
* Show Current Process Slide to Explain process
* Show IaC Slide
    * Introduce Infrastructure As Code and State Management - reusability
* I'll show how we integrate with a version control system like Git abd how we declare our infrastructure
* I'll start with provisioning our infrastructure "from scratch" via Terraform OSS, show the outputs, and explore how we can iterate even further.

---
* **code/terminal**
* Show HCL in `/hashicups-application`
* Declarative language in HCL..etc
* Explain that all this could be in a single project, but it's already been split up into modules.
* Explain purpose of reusable modules… the server module is used

```bash
cd /root/gitclones/hashicups-application
terraform init
terraform plan
terraform apply
```
* Show tfstate - Its very important to store the state file in a secure location because it does contain sensitive data 

---
* **Check** (Sets up TFC)
* Lets migrate our hashicups-cli workspace to Terraform cloud .
* Show /hashicups-application/remote-backend.tf
* Explain that the init process migrates the file to TFC and creates the hashicups-cli workspace.

```bash
cd /root/gitclones/hashicups-application
terraform init
```

* From GitLab show the **HashiCups Application** repos attached with each branch connected to the corresponding Repositories (Prod, Dev Stage).
* Run a plan in **staging**

---
* **Check** (Next we look at modules)
* These modules simplify the overhead consumers go through in building infrastructure from scratch. These standardized (and repeatable!) modules ensure the Terraform configurations adhere to internal best practices and compliance requirements.
* The contributing teams for the module registry might be:
    * Networking Teams
    * Infrastructure Admins
    * Database Teams
    * Security Teams

```bash
cd /root/setup/terraform/tfc-registry
terraform init
terraform apply -auto-approve
```

* In the new TFC hashicups-module workspace trigger a plan. You can also apply it if you want and then connect to the application by right-clicking on the URL at the end of the "output" output.

---
* **Check** (Next we look at Guardrails)
* Review the `cloud-agnostic/pmr/require-all-resources-from-pmr.sentinel` policy in the GitLab
* Explain that Sentinel supports advisory, soft-mandatory, and hard-mandatory enforcement modes and that all of the demo's policy sets use the soft-mandatory option which means that users with suitable permissions can override the violations and still apply the runs.
* In the Settings/Policy Sets show the configured require-all-resources-from-pmr policy set.
* In your hashicups-staging or hashicups-prod workspace, queue a new plan
* observe the automatic triggering of the Sentinel policy.
* you can override the soft-mandatory violations

---
# Summarize
* Common workflow across compute platforms (On-prem + multi-cloud)
* Automated Producer/Consumer model
* Automated policy as code enforcement
* Dramatically reduced time to market/value for new applications and services
* Reusable code templates for use across business units and use cases


# Cleanup
The `track_scripts/cleanup-terraform` script will automatically clean-up your TFC Organization by running destroy plans against all the workspaces and by destroying the hashicups-cli workspace. This facilitates easier re-use of the same TFC organization when you deliver the demo again.

* **Delete VCS Providers manualy**