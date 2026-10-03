# Assignment 5 — Deploy Book Review App in Your Favorite Cloud (Agentic Terraform Project)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

This is the most important assignment of the Terraform section. You will deploy the Book Review App in a production-style three-tier architecture using Terraform on your choice of AWS or Azure — six subnets across two Availability Zones, tier-specific security rules, public and internal load balancers, Next.js/Node.js on Ubuntu VMs, and a private managed MySQL database with a read replica. This assignment is agent-assisted: you may use Claude Code, ChatGPT, or another LLM tool to help design, generate, debug, and improve the infrastructure.

---

# Task 1 — VPC/VNet and Subnet Setup

## Goal

Create a custom VPC/VNet (10.0.0.0/16) with six subnets across two Availability Zones: two public Web Tier subnets, two private App Tier subnets, and two private Database Tier subnets, implemented with Terraform.

### Evidence

#### Screenshot 1 — VPC or VNet details showing 10.0.0.0/16

<img width="988" height="596" alt="Ass5-ss1a" src="https://github.com/user-attachments/assets/75bcaebb-e991-47db-926b-fbd064693972" />
<img width="1011" height="419" alt="Ass5-ss1b" src="https://github.com/user-attachments/assets/16153b17-5f23-405d-a309-1a3f174310b0" />


---

#### Screenshot 2 — Subnet list showing all six subnets, their tiers, CIDR ranges, and Availability Zones

<img width="1337" height="620" alt="Ass5-ss2" src="https://github.com/user-attachments/assets/0432323d-b95f-4c1a-9e02-36a5b1d20e4c" />


---

#### Screenshot 3 — Terraform plan or cloud networking view showing the required routing and tier isolation

<img width="1315" height="745" alt="Ass5-ss3" src="https://github.com/user-attachments/assets/81562956-6b07-4a05-b173-8354ab026644" />


---

# Task 2 — Security Groups/NSGs and Load Balancers

## Goal

Configure tier-specific Security Groups/NSGs (Web Tier HTTP 80, App Tier 3001 only from Web Tier, Database Tier 3306 only from App Tier), and create a public load balancer for the frontend and an internal load balancer for the backend, all with Terraform.

### Evidence

#### Screenshot 4 — Web, App, and Database Security Group or NSG rules



---

#### Screenshot 5 — Public frontend load balancer configuration

<img width="1151" height="319" alt="Ass5-ss5" src="https://github.com/user-attachments/assets/397b0022-2647-4c5d-af0b-6d7b552888d0" />


---

#### Screenshot 6 — Internal backend load balancer configuration

<img width="685" height="334" alt="Ass5-ss6" src="https://github.com/user-attachments/assets/8e706b16-7afd-41b9-beba-ca762e807c7d" />


---

#### Screenshot 7 — Healthy frontend and backend targets or backend pools

<img width="1341" height="447" alt="Ass5-ss7" src="https://github.com/user-attachments/assets/7d56d1fd-dc8a-458e-9b7b-928c0ceab2a1" />


---

# Task 3 — VMs and Application Deployment

## Goal

Deploy the Next.js Web Tier behind Nginx on port 80 in the public subnets, and the Node.js App Tier on port 3001 in the private subnets (no Elastic IPs/Public IPs on private VMs), with the frontend reaching the backend through the internal load balancer.

### Evidence

#### Screenshot 8 — EC2 or Azure VM dashboard showing the frontend and backend VMs

<img width="1188" height="389" alt="Ass5-ss8" src="https://github.com/user-attachments/assets/c1f4d4b5-aa7d-4b4a-a545-9a57fd425125" />


---

#### Screenshot 9 — Nginx status or frontend response on the Web Tier

<img width="1366" height="390" alt="Ass5-ss9" src="https://github.com/user-attachments/assets/60a88893-59d7-4c75-86fa-946489c1180e" />


---

#### Screenshot 10 — Backend API response through the permitted internal path

<img width="1348" height="632" alt="Ass5-ss10" src="https://github.com/user-attachments/assets/6102d10c-1d20-400f-8ff6-07a76e7dfccd" />


---

# Task 4 — MySQL Database Setup

## Goal

Deploy a private managed MySQL database (Amazon RDS Multi-AZ or Azure Database for MySQL Flexible Server) with a read replica, restricted to the App Tier on port 3306, and validate the Book Review App homepage, login, review flow, backend API, and database integration through the public load balancer.

### Evidence

#### Screenshot 11 — Amazon RDS or Azure Database dashboard showing the primary database and read replica

<img width="1344" height="600" alt="Ass5-ss11" src="https://github.com/user-attachments/assets/fc6cd83e-dcf3-4104-af76-87cf20c6ddd5" />


---

#### Screenshot 12 — Evidence of private database networking and permitted App Tier access

<img width="1343" height="562" alt="Ass5-ss12a" src="https://github.com/user-attachments/assets/2b2361d6-cf5b-4d48-8ddb-9f4e3b32214f" />
<img width="1343" height="657" alt="Ass5-ss12b" src="https://github.com/user-attachments/assets/5845cdb8-4070-4c7d-8c53-28467e9a2732" />


---

#### Screenshot 13 — Functional Book Review App homepage and login flow

<img width="1348" height="591" alt="Ass5-ss13" src="https://github.com/user-attachments/assets/01cd4b91-cdec-4eb2-afd6-983200ceda96" />


---

#### Screenshot 14 — Functional review flow with working backend API and database integration

<img width="1344" height="610" alt="Ass5-ss14" src="https://github.com/user-attachments/assets/e98e45a1-00a5-4ffb-91dc-4b542ea17447" />


---

#### Screenshot 15 (optional) — Application logs or terminal output

<img width="1349" height="656" alt="Ass5-ss15" src="https://github.com/user-attachments/assets/2a5167b3-ba80-49e0-88d9-eecc55699cfd" />


---

### Notes

Report the cloud platform used (AWS or Azure), your Terraform code structure (`main.tf`, `variables.tf`, `outputs.tf`, and supporting files), a link/description of your architecture diagram, and the Public Load Balancer DNS used to access the frontend.



---

# LinkedIn Post (Required)

## Goal

Publish a LinkedIn post about what you achieved in this assignment, with public or "Anyone" visibility.

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

#### Screenshot 16 — Published LinkedIn post showing the text and at least one image or proof



---

# Submission Instructions

- Add all required screenshots in your submission
- Include your architecture diagram and Public Load Balancer DNS
- Do not expose passwords, keys, tokens, database credentials, or Terraform state secrets

---

# Completion Checklist

- [ ] Task 1: Six-subnet VPC/VNet created across two AZs with Terraform (Screenshots 1–3)
- [ ] Task 2: Tier-specific security rules and load balancers configured (Screenshots 4–7)
- [ ] Task 3: Web and App Tier VMs deployed with correct public/private placement (Screenshots 8–10)
- [ ] Task 4: Private MySQL with read replica deployed and app validated end to end (Screenshots 11–15)
- [ ] Report completed: cloud platform, Terraform structure, diagram, LB DNS (Notes)
- [ ] LinkedIn post published and URL submitted (Screenshot 16)
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
