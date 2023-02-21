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

* Introduce Infrastructure As Code and State Management - reusability
* I'll show how we integrate with a version control system like Git, how we declare our infrastructure
* I'll start with provisioning our infrastructure "from scratch" via Terraform OSS, show the outputs, and explore how we can iterate even further.
* Show HCL in `/hashicups-application`




---

# Cleanup
The `track_scripts/cleanup-terraform` script will automatically clean-up your TFC Organization by running destroy plans against all the workspaces and by destroying the hashicups-cli workspace. This facilitates easier re-use of the same TFC organization when you deliver the demo again.