# Assignment 3 — Deploy a React Application on Azure Using Terraform

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will use Terraform to provision the required Azure infrastructure and automatically deploy the `my-react-app` React application on an Azure Linux virtual machine using a `cloud-init.sh` deployment script passed to the VM through `custom_data`.

You will verify the automated deployment through SSH, confirm that Nginx is running, access the React application through the VM public IP, and destroy the Terraform-managed resources after testing.

---

# Task 0 — Set Up and Verify the Terraform and Azure CLI Environment

## Goal

Prepare your local environment for Terraform deployment by installing Terraform, Azure CLI, and the HashiCorp Terraform extension in VS Code, signing in to your Azure account, and confirming that all required tools are working correctly.

## Evidence

### Screenshot 1 — Terraform Version

Add a screenshot of the terminal showing successful `terraform version` output.

<img width="739" height="194" alt="Ass3-ss1" src="https://github.com/user-attachments/assets/66957d3c-d46b-4795-8c35-2b1d2e75db62" />


---

### Screenshot 2 — Azure CLI Version

Add a screenshot of the terminal showing successful `az version` output.

Add your screenshot here.

---

### Screenshot 3 — HashiCorp Terraform Extension

Add a screenshot of the VS Code Extensions panel showing the HashiCorp Terraform extension installed and enabled.

Add your screenshot here.

---

# Task 1 — Create a New Terraform Project and Define the Infrastructure

## Goal

Create a new Terraform project and define the complete Azure infrastructure required to host the React application using the official Terraform Registry documentation.

The `terraform-react-azure` project must contain:

```text
terraform-react-azure/
├── main.tf
└── cloud-init.sh
```

The Terraform configuration must include:

- Terraform and AzureRM provider configuration
- Resource group
- Virtual network and subnet
- Network Security Group
- SSH rule for TCP port `22`
- HTTP rule for TCP port `80`
- Public IP address
- Network interface
- Linux virtual machine
- `custom_data` configuration referencing `cloud-init.sh`
- Public IP output

The `cloud-init.sh` file must contain the complete automated React application deployment workflow based on the repository instructions.

## Evidence

### Screenshot 4 — Provider, Resource Group, and Network Security Group

Add a screenshot of VS Code showing the AzureRM provider, resource group, and Network Security Group configuration in `main.tf`.

<img width="791" height="349" alt="Ass3-ss2" src="https://github.com/user-attachments/assets/2a7f7491-48e5-4437-bd81-98be7ffb619f" />


---

### Screenshot 5 — Linux Virtual Machine and `custom_data`

Add a screenshot of VS Code showing the Linux virtual machine configuration, including the `custom_data` configuration, in `main.tf`.

Ensure that passwords, private keys, account IDs, access tokens, and other sensitive information are hidden.

Add your screenshot here.

---

### Screenshot 6 — Completed `cloud-init.sh`

Add a screenshot of VS Code showing the completed `cloud-init.sh` deployment script.

Ensure that no passwords, Azure credentials, access tokens, SSH private keys, or other sensitive information are visible.

Add your screenshot here.

---

### Screenshot 7 — Public IP Output Block

Add a screenshot of VS Code showing the public IP `output` block in `main.tf`.

Add your screenshot here.

---

# Task 2 — Initialize Terraform

## Goal

Initialize the Terraform working directory and download the required provider components.

## Evidence

### Screenshot 8 — Terraform Initialization

Add a screenshot of the terminal showing successful `terraform init` output.

<img width="1098" height="629" alt="Ass3-ss3" src="https://github.com/user-attachments/assets/d4b2c280-b27e-4968-a34a-402c83518f92" />


---

# Task 3 — Plan and Apply the Configuration

## Goal

Review the Terraform execution plan and provision the Azure infrastructure.

## Evidence

### Screenshot 9 — Terraform Plan

Add a screenshot showing the Terraform plan summary and the proposed resources.

<img width="691" height="508" alt="Ass3-ss4a" src="https://github.com/user-attachments/assets/f27d1967-9740-4393-9cf0-920bad185781" />
<img width="636" height="577" alt="Ass3-ss4b" src="https://github.com/user-attachments/assets/3d8f0038-d5b5-49c1-a76b-1c41dd8a47de" />


---

### Screenshot 10 — Terraform Apply

Add a screenshot showing successful `terraform apply` completion.

<img width="698" height="507" alt="Ass3-ss5" src="https://github.com/user-attachments/assets/6d7b4e43-a074-4941-953a-f04800d8e296" />
<img width="630" height="270" alt="Ass3-ss5a" src="https://github.com/user-attachments/assets/e0e05cc0-9b28-4652-b60e-90a5d28997ea" />


---

### Screenshot 11 — VM Public IP Output

Add a screenshot showing the VM public IP address returned by `terraform output`.

Add your screenshot here.

## VM Public IP Address

Record the public IP address displayed by `terraform output`.

**VM Public IP Address:** Add the VM public IP address here

---

# Task 4 — Verify the Automated Deployment

## Goal

Connect to the Azure Linux virtual machine and confirm that the cloud-init/user data deployment script completed successfully.

## Evidence

### Screenshot 12 — SSH Connection and Completed React Deployment

Add a screenshot of SSH terminal showing successful connection to the Azure VM and evidence that the React application deployment completed such as the deployed files in `/var/www/html` or successful cloud-init output.

<img width="693" height="128" alt="Ass3-ss6" src="https://github.com/user-attachments/assets/bbc4e931-11d7-4da4-990c-6b41867cf0da" />


---

### Screenshot 13 — Nginx Service Status

Add a screenshot of the terminal showing that the Nginx service is running successfully.

Add your screenshot here.

---

# Task 5 — Verify the React Application Deployment

## Goal

Confirm that the automatically deployed React application is publicly accessible and functioning correctly.

## Evidence

### Screenshot 14 — React Application in the Browser

Add a screenshot of the browser showing the deployed React application successfully loaded using the Azure VM public IP.

Ensure that the Azure VM public IP is visible in the browser address bar.

<img width="509" height="215" alt="Ass3-ss7" src="https://github.com/user-attachments/assets/bb4ebd49-200c-4f42-a62c-2ae3b3f04abd" />


---

# Task 6 — Destroy the Resources

## Goal

Remove all Azure resources created by Terraform after completing the application deployment and verification.

## Evidence

### Screenshot 15 — Terraform Destroy

Add a screenshot of the terminal showing successful `terraform destroy` completion.

<img width="707" height="333" alt="Ass3-ss8" src="https://github.com/user-attachments/assets/4b739cc3-3b27-4493-aa11-e05e25afe5f0" />


---

<<<<<<< HEAD
# Task 7 — Share Your Deployment Progress on LinkedIn
=======
#### Screenshot 9 — Terminal showing that Nginx is active and running

<img width="747" height="516" alt="Ass3-ss9" src="https://github.com/user-attachments/assets/bf10d6a0-3e6c-48a7-9392-f04ccb30f63d" />


---

# Task 8 — Test the Deployment
>>>>>>> fa0fe3f5940441fa375cf0fca9c1c3c1fc878c30

## Goal

Share your React application deployment progress and DMI Leaderboard link on LinkedIn.

## Steps

1. Open the DMI Leaderboard and find your name.
2. Select **Share your progress**.
3. Select the **LinkedIn** option.
4. Use the generated message containing your leaderboard rank and personal progress link.
5. Attach **Screenshot 14** showing your React application running in the browser.
6. Add this caption:

```text
Just deployed a React application on an Azure Virtual Machine using Terraform! ☁️

I provisioned the Azure infrastructure with Terraform and automated the React application deployment using cloud-init Custom Data and Nginx.

Check my DMI learning progress below. 🚀
```

7. Publish the post on LinkedIn.

## Evidence

### Screenshot 16 — LinkedIn Post

Add a screenshot of your published LinkedIn post showing:

- The React application deployment screenshot
- The generated DMI Leaderboard message
- Your personal DMI progress link

Ensure that no passwords, private keys, account IDs, access tokens, or other sensitive information are visible.

<img width="766" height="419" alt="Ass3-ss10" src="https://github.com/user-attachments/assets/d9961c30-1fba-4ddd-a9ad-73825e5f457d" />


---

<<<<<<< HEAD
=======
### Notes

Write a short summary of what you built and any issues you encountered and how you resolved them.



---

>>>>>>> fa0fe3f5940441fa375cf0fca9c1c3c1fc878c30
# Submission Instructions

- Complete Tasks 0–7 in sequence.
- Include all 16 required screenshots exactly as specified.
- Ensure that your full name is visible in the required screenshots.
- Record the VM public IP address under Task 3.
- Ensure that the submitted evidence clearly matches the required task outputs.
- Include `main.tf` and `cloud-init.sh` in your GitHub submission.
- Do not expose passwords, SSH private keys, account IDs, access tokens, Azure credentials, or other sensitive information.
- Do not store secrets inside `cloud-init.sh`.
- Review all screenshots and project files carefully before submitting through GitHub.

---

# Completion Checklist

- [ ] Installed Terraform and verified it using `terraform version`
- [ ] Installed Azure CLI and verified it using `az version`
- [ ] Signed in to Azure and confirmed the correct subscription
- [ ] Installed and enabled the HashiCorp Terraform extension in VS Code
- [ ] Created the `terraform-react-azure` project
- [ ] Created `main.tf`
- [ ] Defined the Terraform and AzureRM provider configuration
- [ ] Defined the resource group
- [ ] Defined the virtual network and subnet
- [ ] Defined the Network Security Group
- [ ] Configured SSH and HTTP rules
- [ ] Defined the public IP and network interface
- [ ] Created `cloud-init.sh`
- [ ] Reviewed the React application repository instructions
- [ ] Created the complete deployment workflow inside `cloud-init.sh`
- [ ] Defined the Linux virtual machine
- [ ] Connected `cloud-init.sh` to the VM using `custom_data`
- [ ] Used `file()` and `base64encode()` correctly
- [ ] Added the Terraform public IP output
- [ ] Completed `terraform init` successfully
- [ ] Reviewed the Terraform execution plan
- [ ] Completed `terraform apply` successfully
- [ ] Recorded the VM public IP
- [ ] Connected to the VM through SSH
- [ ] Verified that the automated deployment completed successfully
- [ ] Verified that Nginx is running
- [ ] Verified the React application through the browser
- [ ] Completed `terraform destroy` successfully
- [ ] Shared the React application deployment progress on LinkedIn by following Task 7
- [ ] Captured all 16 required screenshots
- [ ] Confirmed that my full name is visible in the required screenshots
- [ ] Checked that no passwords, keys, account IDs, access tokens, or other sensitive information are exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations through hands-on experience.

---

## Resources

- React Application Repository: [https://github.com/pravinmishraaws/my-react-app](https://github.com/pravinmishraaws/my-react-app)
- DMI Official Website: [https://dmi.pravinmishra.com](https://dmi.pravinmishra.com)
- University: [https://university.pravinmishra.com](https://university.pravinmishra.com)
- Discord Community: [https://discord.pravinmishra.com](https://discord.pravinmishra.com)
- Blog: [https://dmi.pravinmishra.com/blog](https://dmi.pravinmishra.com/blog)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra on LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory on LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of the DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
