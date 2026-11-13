# Assignment 1 — Configure a Self-Hosted Azure DevOps Agent on Ubuntu

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will provision an Ubuntu VM in AWS or Azure and configure it as a self-hosted Azure Pipelines agent. You will create an agent pool, register the agent using a Personal Access Token (PAT), run it as a Linux system service, and verify it by executing a test pipeline on the VM.

---

# Task 0 — Create or Access Azure DevOps

## Goal

Sign in to Azure DevOps and create or access an organization and project for the assignment.

No submission screenshot is required for this task.

---

# Task 1 — Create a Personal Access Token (PAT)

## Goal

Create and securely store the PAT required to register the self-hosted agent.

No submission screenshot is required for this task.

> Do not include the PAT in this document or in any screenshot.

---

# Task 2 — Create a Self-Hosted Agent Pool

## Goal

Create the Azure DevOps agent pool that will contain the Linux agent.

No submission screenshot is required for this task.

---

# Task 3 — Provision and Connect to the Ubuntu VM

## Goal

Provision an Ubuntu VM in AWS or Azure and verify its operating system, architecture, and outbound connection to Azure DevOps.

## Evidence

### Screenshot 1 — Ubuntu VM Running

Add a screenshot from AWS or Azure showing:

* Ubuntu VM name
* VM status as **Running**
* Public IP address

<img width="1359" height="565" alt="Ass1-ss1" src="https://github.com/user-attachments/assets/69eb450d-1d3c-44d3-8187-d983415b2d53" />


---

### Screenshot 2 — Ubuntu, Architecture, and HTTPS Verification

Add an SSH terminal screenshot showing the output of:

* `cat /etc/os-release`
* `uname -m`
* `curl -I https://dev.azure.com`

The screenshot must confirm a supported Ubuntu version, `x86_64` architecture, and a successful HTTP response from Azure DevOps.

<img width="530" height="522" alt="Ass1-ss2" src="https://github.com/user-attachments/assets/50ef4f13-4588-4eb4-aff2-347b24384f6a" />


---

# Task 4 — Install and Configure the Azure Pipelines Agent

## Goal

Download, configure, and register the Linux Azure Pipelines agent, and run it as a system service.

## Evidence

### Screenshot 3 — Agent Configuration and Service Status

Add a terminal screenshot showing:

* Successful agent configuration
* Agent service installation
* Agent service start
* `sudo ./svc.sh status` reporting that the service is running

<img width="851" height="707" alt="Ass1-ss3" src="https://github.com/user-attachments/assets/12cd0003-dcdb-4be8-a727-fb1c01ebebf9" />


> Ensure that the PAT is not visible.

---

# Task 5 — Verify That the Agent Is Online

## Goal

Confirm that the agent service is running and the agent appears online in Azure DevOps.

## Evidence

### Screenshot 4 — Agent Online in Azure DevOps

Add a screenshot of the Azure DevOps Agent Pool **Agents** page showing:

* Selected agent pool
* Selected agent name
* Agent status as **Online**
* Agent enabled and available

<img width="1037" height="718" alt="Ass1-ss4" src="https://github.com/user-attachments/assets/59fae4d4-0171-4316-8d37-8f6a3045c234" />


---

# Task 6 — Create and Run a Test Pipeline

## Goal

Create an Azure DevOps YAML pipeline and verify that its commands execute on the self-hosted Ubuntu VM.

## Evidence

### Screenshot 5 — Azure Pipelines YAML

Add a screenshot of `azure-pipelines.yml` open in the Azure Repos editor showing:

* `trigger: none`
* Selected self-hosted agent pool
* Bash verification step
* Your Full Name
* Linux verification commands

<img width="1092" height="580" alt="Ass1-ss5" src="https://github.com/user-attachments/assets/964625d2-1982-459b-a32f-f6aeb41ab838" />


---

### Screenshot 6 — Successful Test Pipeline

Add a screenshot of the successful Azure DevOps pipeline run showing:

* Overall status as **Succeeded**
* Expanded **Verify self-hosted Ubuntu agent** step
* `Submitted by: <your-full-name>`
* Agent name
* Machine name
* Output from `uname -a`
* Output from `whoami`
* Output from `df -h`
* Output from `pwd`

<img width="1352" height="638" alt="Ass1-ss6" src="https://github.com/user-attachments/assets/1f3aa413-61aa-4fb9-97cb-3fc3cdb4fe57" />


---

## Completed azure-pipelines.yml

Paste the contents of your completed `azure-pipelines.yml` file below.

```yaml

```

> Do not include your PAT, SSH private key, password, or cloud credentials in the YAML file.

---

# Assignment Summary

Write a short summary of what you configured.

I successfully provisioned an Ubuntu virtual machine on AWS and configured it as a self-hosted Azure DevOps agent. I created an Azure DevOps Personal Access Token (PAT) and agent pool, downloaded and configured the Azure Pipelines agent, and registered it with Azure DevOps. I installed and started the agent as a Linux system service and verified that it was running and showing as Online in the Azure DevOps agent pool. Finally, I created and executed a YAML test pipeline on the self-hosted agent, successfully verifying the Ubuntu environment, agent identity, machine information, disk space, and working directory.

---

# LinkedIn Requirement (If Applicable)

## Screenshot 7 — LinkedInisor填Token Belle

Add a screenshot of your LinkedIn post showing:

* What you configured
* Why organizations use self-hosted agents
* Three to five lines explaining your experience
* A screenshot of the successful pipeline run with no secrets visible



**LinkedIn Post URL:** 

---

# Submission Instructions

* Include the short assignment summary.
* Include Screenshots 1–6.
* Include the contents of your completed `azure-pipelines.yml` file.
* Include Screenshot 7 and the LinkedIn post URL if the LinkedIn requirement applies.
* Do not expose a PAT, SSH private key, password, account details, or another secret.

---

# Completion Checklist

* Azure DevOps organization and project are ready
* A supported Ubuntu LTS VM is running and accessible through SSH
* SSH access is restricted to your public IP address
* Outbound HTTPS connectivity is working
* PAT was created with the required scopes and stored securely
* A self-hosted agent pool was created
* The same pool name was used during registration and in the pipeline YAML
* The agent service is running
* The agent appears **Online** in Azure DevOps
* The pipeline targets the selected agent pool
* The pipeline run completed with **Succeeded** status
* The pipeline output displays your Full Name
* Screenshots 1–6 are included and readable
* Screenshot 7 and the LinkedIn post URL are included if applicable
* The completed `azure-pipelines.yml` content is included
* No PAT, SSH private key, password, or other secret is visible

---

*This submission is part of the DevOps Micro Internship (DMI) — Agentic AI Track.*
