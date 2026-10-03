# Assignment 4 — Deploy EpicBook Application on AWS Using Terraform

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will use Terraform to provision AWS network infrastructure (VPC, public/private subnets, Security Groups), launch an Ubuntu 22.04 EC2 instance, and provision a private Amazon RDS for MySQL instance. You will then deploy EpicBook, connect it to MySQL, and validate the complete user flow.

---

# Task 1 — Create Network Infrastructure with Terraform

## Goal

Define a VPC (10.0.0.0/16) with a public subnet (10.0.1.0/24) and private subnet (10.0.2.0/24), an Internet Gateway with public routing, an EC2 Security Group (SSH 22, HTTP 80), and an RDS Security Group (MySQL 3306 only from the EC2 Security Group).

### Evidence

#### Screenshot 1 — Terraform configuration showing the VPC and both subnet CIDR ranges

<img width="694" height="128" alt="Ass4-ss1" src="https://github.com/user-attachments/assets/33a429cf-6347-44e2-b444-1a769c69b08a" />


---

#### Screenshot 2 — Terraform configuration showing the Internet Gateway, public route table, and both Security Groups

<img width="427" height="102" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/3a94a58e-b995-4951-b62f-3969ba665248" />


---

# Task 2 — Provision EC2 Virtual Machine (Ubuntu 22.04)

## Goal

Use Terraform to launch a t2.micro Ubuntu 22.04 EC2 instance in the public subnet with a public IP, then install Node.js, npm, Git, Nginx, and MySQL client.

### Evidence

#### Screenshot 3 — Terraform apply output showing successful EC2 provisioning

<img width="1343" height="661" alt="Ass4-ss3" src="https://github.com/user-attachments/assets/3f850c00-ceec-4db8-8df8-05b1cc4e4ef1" />


---

#### Screenshot 4 — EC2 instance running in the AWS Console with the public IP and subnet visible

<img width="531" height="432" alt="Ass4-ss4" src="https://github.com/user-attachments/assets/b1d35560-664c-4611-ab64-6a154d9b1223" />


---

#### Screenshot 5 — Terminal showing successful SSH access and installed software

<img width="1296" height="653" alt="Ass4-ss5" src="https://github.com/user-attachments/assets/d27a8788-d36b-4baa-a4cc-d590bd8b1eed" />


---

# Task 3 — Deploy the EpicBook Application

## Goal

Deploy the EpicBook frontend and backend on the EC2 instance and configure Nginx to serve it, following the Installation, Configuration & Troubleshooting Guide.

### Evidence

#### Screenshot 6 — Terminal showing the EpicBook application files and dependency installation

<img width="1339" height="624" alt="Ass4-ss6" src="https://github.com/user-attachments/assets/04e48e5d-dd1c-4fec-a6c8-fcb4a6fbef5e" />


---

#### Screenshot 7 — Terminal showing the application and Nginx services running

<img width="1355" height="603" alt="Ass4-ss7a" src="https://github.com/user-attachments/assets/a271215f-7266-4c77-9376-1cb55ff4bb18" />
<img width="1356" height="593" alt="Ass4-ss7b" src="https://github.com/user-attachments/assets/6dc7a172-e36b-4194-889d-bcb4b3381461" />


---

# Task 4 — Set Up Amazon RDS for MySQL with Terraform

## Goal

Provision a private Amazon RDS MySQL instance (db.t3.micro, Publicly accessible: false) restricted to the EC2 Security Group, then initialize the database using the provided SQL dump and connect the EpicBook backend to it.

### Evidence

#### Screenshot 8 — Terraform apply output showing successful RDS provisioning

<img width="1359" height="491" alt="Ass4-ss8" src="https://github.com/user-attachments/assets/a7c13eb1-e6f4-4f9f-b405-a21db8cf43dd" />


---

#### Screenshot 9 — RDS instance in the AWS Console showing the private network configuration and Publicly accessible: No

<img width="1353" height="673" alt="Ass4-ss9" src="https://github.com/user-attachments/assets/13406b52-6f2b-44b3-876f-54c4eb8776d0" />


---

#### Screenshot 10 — Terminal showing successful database initialization or table verification from EC2

<img width="1348" height="487" alt="Ass4-ss10" src="https://github.com/user-attachments/assets/e190fc4e-33e8-45a5-9e65-40cc11536243" />


---

# Task 5 — Test End-to-End Functionality

## Goal

Confirm EpicBook is accessible through the EC2 public IP and that navigation, cart, order summary, and checkout all work against the MySQL backend.

### Evidence

#### Screenshot 11 — Browser showing the EpicBook application through the EC2 public IP

<img width="1343" height="583" alt="Ass4-ss11a" src="https://github.com/user-attachments/assets/1761a9cf-9df0-4594-be22-94ca6fdbbc01" />
<img width="1363" height="557" alt="Ass4-ss11b" src="https://github.com/user-attachments/assets/73261d85-c9e6-4941-b8d0-0159ac93b179" />


---

#### Screenshot 12 — Browser showing a working product, cart, order summary, or checkout flow

<img width="1349" height="379" alt="Ass4-ss12" src="https://github.com/user-attachments/assets/ea8ca3b4-f271-4b8a-9259-62cb0539e25e" />


---

### Notes

Write a short note describing any issue you faced, how you fixed it, and what you learned.



---

# LinkedIn Post (Required)

## Goal

Publish a LinkedIn post about what you achieved in this assignment, with public or "Anyone" visibility.

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

#### Screenshot 13 — Published LinkedIn post showing the text and at least one image or proof



---

# Submission Instructions

- Add all required screenshots in your submission
- Include the EC2 public IP
- Do not expose database passwords, private keys, or other secrets

---

# Completion Checklist

- [ ] Task 1: VPC, subnets, IGW, and Security Groups created with Terraform (Screenshots 1–2)
- [ ] Task 2: EC2 provisioned and required software installed (Screenshots 3–5)
- [ ] Task 3: EpicBook deployed and Nginx serving the app (Screenshots 6–7)
- [ ] Task 4: Private RDS MySQL created and database initialized (Screenshots 8–10)
- [ ] Task 5: End-to-end functionality validated (Screenshots 11–12)
- [ ] Issue/fix/learning note written (Notes)
- [ ] LinkedIn post published and URL submitted (Screenshot 13)
- [ ] No sensitive data exposed

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
