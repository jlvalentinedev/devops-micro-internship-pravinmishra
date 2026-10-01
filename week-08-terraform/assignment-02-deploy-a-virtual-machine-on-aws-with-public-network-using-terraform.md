# Assignment 2 — Deploy a Virtual Machine on AWS with Public Network Using Terraform

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will use Terraform to create a custom AWS network (VPC, public and private subnets, Internet Gateway, route table) and launch an EC2 instance into the public subnet with a public IP, a Security Group allowing SSH and HTTP, and Nginx installed for validation.

---

# Task 1 — Create a New Terraform Project

## Goal

Create a `terraform-aws-vm` project directory for the AWS Terraform configuration.

### Evidence

#### Screenshot 1 — File Explorer, VS Code, or terminal showing the `terraform-aws-vm` project directory

![terraform](screenshots/tf-assignment2task1.png)

---

# Task 2 — Create main.tf with the Required AWS Resources

## Goal

Define the AWS provider, a VPC (10.0.0.0/16) with a public subnet (10.0.1.0/24) and private subnet (10.0.2.0/24), an Internet Gateway with public routing, a Security Group (SSH 22, HTTP 80), an EC2 instance in the public subnet with a public IP, and a public IP output.

### Evidence

#### Screenshot 2 (optional) — `main.tf` showing the VPC and EC2 resource blocks

![terraform](screenshots/tf-assignment2task2_1.png)

---
![terraform](screenshots/tf-assignment2task2.png)


# Task 3 — Initialize Terraform

## Goal

Run `terraform init` and confirm the working directory initializes successfully.

### Evidence

#### Screenshot 3 — Terminal showing successful `terraform init` output

![terraform](screenshots/tf-assignment2screen3.png)

---

# Task 4 — Plan and Apply the Configuration

## Goal

Review `terraform plan`, run `terraform apply`, and record the EC2 instance's public IP from the Terraform output.

### Evidence

#### Screenshot 4 — Terraform apply output showing successful completion

![terraform](screenshots/tf-assignmenttask4.png)
---
![terraform](screenshots/tf-task4screenshot4.png)

#### Screenshot 5 — Terraform output showing the EC2 public IP

![terraform](screenshots/tf-assignment2screen5.png)

---

# Task 5 — Verify the Deployment

## Goal

Confirm the EC2 instance is running in the public subnet with a public IP, install Nginx, and confirm it is accessible by browser or SSH.

### Evidence

#### Screenshot 6 — EC2 instance running in the AWS Console, with the subnet and public IP visible

Add your screenshot here.

---

#### Screenshot 7 — Browser showing the Nginx page through the EC2 public IP, or terminal showing a successful SSH connection

![terraform](screenshots/tf-task5screenshot7.png)

---
![terraform](screenshots/tf-ngnix.png)

# Task 6 — Destroy Resources

## Goal

Run `terraform destroy` to remove the Terraform-managed AWS resources after testing.

### Evidence

#### Screenshot 8 — Terminal showing successful `terraform destroy` completion

![terraform](screenshots/tf-destroy.png)

---

### Notes

Write a short paragraph about any challenges you faced and how you solved them.

One challenge I faced during this project was not initially seeing my EC2 instance in the AWS Console because I was viewing the wrong AWS region. I solved this by switching to the Stockholm (`eu-north-1`) region where Terraform created the resources. I also initially received a connection error when accessing the EC2 public IP because Nginx had not been installed and started. I connected to the instance using SSH, installed Nginx, started the service, and verified that it was running. After these steps, I was able to access the Nginx welcome page through the EC2 public IP.


---

# Submission Instructions

- Add all required screenshots in your submission
- Include the EC2 public IP
- Do not expose AWS credentials, private keys, or account IDs

---

# Completion Checklist

- [✅] Task 1: `terraform-aws-vm` project created (Screenshot 1)
- [✅] Task 2: `main.tf` defines VPC, subnets, IGW, Security Group, and EC2 (Screenshot 2, optional)
- [✅] Task 3: `terraform init` completed successfully (Screenshot 3)
- [✅] Task 4: Plan reviewed and `terraform apply` completed, public IP recorded (Screenshots 4–5)
- [✅] Task 4: Plan reviewed and `terraform apply` completed, public IP recorded (Screenshots 4–5)
- [✅] Task 4: Plan reviewed and `terraform apply` completed, public IP recorded (Screenshots 4–5)
- [✅] Task 5: EC2 instance verified running and accessible (Screenshots 6–7)
- [✅] Task 6: `terraform destroy` completed successfully (Screenshot 8)
- [✅] Challenges/solutions paragraph written (Notes)
- [✅] No sensitive information exposed

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
