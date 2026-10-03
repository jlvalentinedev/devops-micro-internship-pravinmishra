# Assignment 3 — Deploy a React Application on Azure Virtual Machine Using Terraform

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will use Terraform to provision an Azure resource group, network, and Ubuntu 20.04 VM, then deploy the `my-react-app` React application onto the VM over SSH and serve it through Nginx.

---

# Task 1 — Create a New Terraform Project

## Goal

Create a `terraform-react-azure` project directory for the Azure Terraform configuration.

### Evidence

#### Screenshot 1 — File Explorer, VS Code, or terminal showing the `terraform-react-azure` project directory

<img width="739" height="194" alt="Ass3-ss1" src="https://github.com/user-attachments/assets/66957d3c-d46b-4795-8c35-2b1d2e75db62" />


---

# Task 2 — Write main.tf to Provision the Azure Infrastructure

## Goal

Define the resource group, virtual network/subnet, Network Security Group (SSH 22, HTTP 80), public IP, network interface, and Ubuntu 20.04 Standard B1s VM in `main.tf`.

### Evidence

#### Screenshot 2 — VS Code showing `main.tf` with the required Azure resources, with any password or sensitive values hidden

<img width="791" height="349" alt="Ass3-ss2" src="https://github.com/user-attachments/assets/2a7f7491-48e5-4437-bd81-98be7ffb619f" />


---

# Task 3 — Initialize Terraform

## Goal

Run `terraform init` and confirm the working directory initializes successfully.

### Evidence

#### Screenshot 3 — Terminal showing successful `terraform init` output

<img width="1098" height="629" alt="Ass3-ss3" src="https://github.com/user-attachments/assets/d4b2c280-b27e-4968-a34a-402c83518f92" />


---

# Task 4 — Plan and Apply the Configuration

## Goal

Review `terraform plan`, run `terraform apply`, and record the VM's public IP.

### Evidence

#### Screenshot 4 — Terraform apply output showing successful completion

<img width="691" height="508" alt="Ass3-ss4a" src="https://github.com/user-attachments/assets/f27d1967-9740-4393-9cf0-920bad185781" />
<img width="636" height="577" alt="Ass3-ss4b" src="https://github.com/user-attachments/assets/3d8f0038-d5b5-49c1-a76b-1c41dd8a47de" />


---

#### Screenshot 5 — Azure portal showing the Virtual Machine running and its public IP

<img width="698" height="507" alt="Ass3-ss5" src="https://github.com/user-attachments/assets/6d7b4e43-a074-4941-953a-f04800d8e296" />
<img width="630" height="270" alt="Ass3-ss5a" src="https://github.com/user-attachments/assets/e0e05cc0-9b28-4652-b60e-90a5d28997ea" />


---

# Task 5 — Connect to the Virtual Machine

## Goal

Establish an SSH session with the Ubuntu VM through its public IP.

### Evidence

#### Screenshot 6 — Terminal showing a successful SSH connection to the Azure VM

<img width="693" height="128" alt="Ass3-ss6" src="https://github.com/user-attachments/assets/bbc4e931-11d7-4da4-990c-6b41867cf0da" />


---

# Task 6 — Install Node.js, npm, and Git

## Goal

Update Ubuntu and install Node.js, npm, and Git.

### Evidence

#### Screenshot 7 — Terminal showing successful installation and the `node -v` and `npm -v` output

<img width="509" height="215" alt="Ass3-ss7" src="https://github.com/user-attachments/assets/bb4ebd49-200c-4f42-a62c-2ae3b3f04abd" />


---

# Task 7 — Clone, Build, and Serve the React App with Nginx

## Goal

Follow the `my-react-app` repository README to clone, install, and build the app, then serve the production build through Nginx.

### Evidence

#### Screenshot 8 — Terminal showing the successful React build

<img width="707" height="333" alt="Ass3-ss8" src="https://github.com/user-attachments/assets/4b739cc3-3b27-4493-aa11-e05e25afe5f0" />


---

#### Screenshot 9 — Terminal showing that Nginx is active and running

<img width="747" height="516" alt="Ass3-ss9" src="https://github.com/user-attachments/assets/bf10d6a0-3e6c-48a7-9392-f04ccb30f63d" />


---

# Task 8 — Test the Deployment

## Goal

Confirm the React application loads through the VM's public IP and navigation works.

### Evidence

#### Screenshot 10 — Browser showing the React application with the Azure VM public IP visible in the address bar

<img width="766" height="419" alt="Ass3-ss10" src="https://github.com/user-attachments/assets/d9961c30-1fba-4ddd-a9ad-73825e5f457d" />


---

### Notes

Write a short summary of what you built and any issues you encountered and how you resolved them.



---

# Submission Instructions

- Add all required screenshots in your submission
- Include the Azure VM public IP
- Do not expose Azure credentials, passwords, or private keys

---

# Completion Checklist

- [ ] Task 1: `terraform-react-azure` project created (Screenshot 1)
- [ ] Task 2: `main.tf` defines all required Azure resources (Screenshot 2)
- [ ] Task 3: `terraform init` completed successfully (Screenshot 3)
- [ ] Task 4: Plan applied and VM running with public IP (Screenshots 4–5)
- [ ] Task 5: SSH connection verified (Screenshot 6)
- [ ] Task 6: Node.js, npm, and Git installed (Screenshot 7)
- [ ] Task 7: React app built and served through Nginx (Screenshots 8–9)
- [ ] Task 8: App verified through the VM public IP (Screenshot 10)
- [ ] Summary paragraph written (Notes)
- [ ] No sensitive information exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
