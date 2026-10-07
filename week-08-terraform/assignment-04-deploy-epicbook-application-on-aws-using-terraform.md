# Assignment 4 — Deploy EpicBook Web App on AWS Using Terraform Modules and Amazon RDS for MySQL

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will use reusable Terraform modules to provision the AWS infrastructure required by EpicBook. You will create a custom VPC, one public subnet, two private database subnets across different Availability Zones, an Internet Gateway, a public route table, Security Groups, an EC2 Linux instance, and a private Amazon RDS for MySQL database.

You will use EC2 `user_data` to install the required software, initialize the EpicBook database, connect the application to Amazon RDS, configure Nginx, validate the complete browser-to-database workflow, destroy the resources after testing, and publish the required LinkedIn post.

---

# Task 0 — Set Up and Verify the Terraform and AWS CLI Environment

## Goal

<<<<<<< HEAD
Prepare your local environment by installing Terraform, AWS CLI, and the HashiCorp Terraform extension in VS Code, configuring AWS CLI, and confirming that all required tools are working correctly.
=======
Define a VPC (10.0.0.0/16) with a public subnet (10.0.1.0/24) and private subnet (10.0.2.0/24), an Internet Gateway with public routing, an EC2 Security Group (SSH 22, HTTP 80), and an RDS Security Group (MySQL 3306 only from the EC2 Security Group).

### Evidence

#### Screenshot 1 — Terraform configuration showing the VPC and both subnet CIDR ranges

<img width="694" height="128" alt="Ass4-ss1" src="https://github.com/user-attachments/assets/30b2c5f8-c4e1-45e1-ad01-335bd06e7c56" />



---

#### Screenshot 2 — Terraform configuration showing the Internet Gateway, public route table, and both Security Groups

<img width="427" height="102" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/113e210d-afc3-4aaa-a46e-e8f26533767d" />



---

# Task 2 — Provision EC2 Virtual Machine (Ubuntu 22.04)

## Goal

Use Terraform to launch a t2.micro Ubuntu 22.04 EC2 instance in the public subnet with a public IP, then install Node.js, npm, Git, Nginx, and MySQL client.

### Evidence

#### Screenshot 3 — Terraform apply output showing successful EC2 provisioning

<img width="1343" height="661" alt="Ass4-ss3" src="https://github.com/user-attachments/assets/545e4b9f-50ab-4e71-aa85-36b71930f3ba" />



---

#### Screenshot 4 — EC2 instance running in the AWS Console with the public IP and subnet visible

<img width="531" height="432" alt="Ass4-ss4" src="https://github.com/user-attachments/assets/867ef3c3-1825-4c74-90a3-19be7a18890b" />



---

#### Screenshot 5 — Terminal showing successful SSH access and installed software

<img width="1296" height="653" alt="Ass4-ss5" src="https://github.com/user-attachments/assets/2c9c07be-4a55-4abc-a052-57bc56064449" />



---

# Task 3 — Deploy the EpicBook Application

## Goal

Deploy the EpicBook frontend and backend on the EC2 instance and configure Nginx to serve it, following the Installation, Configuration & Troubleshooting Guide.

### Evidence

#### Screenshot 6 — Terminal showing the EpicBook application files and dependency installation

<img width="1339" height="624" alt="Ass4-ss6" src="https://github.com/user-attachments/assets/36de15cf-8244-4038-9130-949af72cf058" />



---

#### Screenshot 7 — Terminal showing the application and Nginx services running

<img width="1355" height="603" alt="Ass4-ss7a" src="https://github.com/user-attachments/assets/f625f8e9-7381-4322-8b82-41969f5f54d9" />
<img width="1356" height="593" alt="Ass4-ss7b" src="https://github.com/user-attachments/assets/2ad2e567-c0da-4cd0-9017-5fbce0a2e99c" />




---

# Task 4 — Set Up Amazon RDS for MySQL with Terraform

## Goal

Provision a private Amazon RDS MySQL instance (db.t3.micro, Publicly accessible: false) restricted to the EC2 Security Group, then initialize the database using the provided SQL dump and connect the EpicBook backend to it.

### Evidence

#### Screenshot 8 — Terraform apply output showing successful RDS provisioning

<img width="1359" height="491" alt="Ass4-ss8" src="https://github.com/user-attachments/assets/9606276b-94fb-408f-91e7-77211add5e3f" />



---

#### Screenshot 9 — RDS instance in the AWS Console showing the private network configuration and Publicly accessible: No

<img width="1353" height="673" alt="Ass4-ss9" src="https://github.com/user-attachments/assets/86f786a0-d94f-49f9-ba4f-0885fd054517" />



---

#### Screenshot 10 — Terminal showing successful database initialization or table verification from EC2

<img width="1348" height="487" alt="Ass4-ss10" src="https://github.com/user-attachments/assets/9d4794bc-a225-452f-bbc8-cfbb283edde8" />



---

# Task 5 — Test End-to-End Functionality

## Goal

Confirm EpicBook is accessible through the EC2 public IP and that navigation, cart, order summary, and checkout all work against the MySQL backend.

### Evidence

#### Screenshot 11 — Browser showing the EpicBook application through the EC2 public IP


<img width="1343" height="583" alt="Ass4-ss11a" src="https://github.com/user-attachments/assets/d54110fd-0dab-40f7-a54b-b49e8cdc8c8c" />
<img width="1363" height="557" alt="Ass4-ss11b" src="https://github.com/user-attachments/assets/b382c3c9-4492-4a19-b807-e03aa3935e28" />



---

#### Screenshot 12 — Browser showing a working product, cart, order summary, or checkout flow

<img width="1349" height="379" alt="Ass4-ss12" src="https://github.com/user-attachments/assets/8544a39f-55e7-4e03-8979-10270aad3e7a" />



---

### Notes

Write a short note describing any issue you faced, how you fixed it, and what you learned.



---

# LinkedIn Post (Required)

## Goal

Publish a LinkedIn post about what you achieved in this assignment, with public or "Anyone" visibility.
>>>>>>> fa0fe3f5940441fa375cf0fca9c1c3c1fc878c30

## Evidence

### Screenshot 1 — Terraform Version

<img width="694" height="128" alt="Ass4-ss1" src="https://github.com/user-attachments/assets/a1575f98-fee0-48af-bc97-cdf92a7ea83d" />




=======


---

### Screenshot 2 — AWS CLI Version


<img width="427" height="102" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/4df150b3-0c44-4926-a716-9c101a6fd137" />



---

### Screenshot 3 — HashiCorp Terraform Extension

Add a screenshot of VS Code showing the HashiCorp Terraform extension installed and enabled.

<img width="1343" height="661" alt="Ass4-ss3" src="https://github.com/user-attachments/assets/1f60b858-d7c6-42a5-a17e-55c91e05c70c" />


---

# Task 1 — Create the Modular Terraform Project

## Goal

Create the Terraform project and organize the AWS infrastructure into separate Network, EC2, and RDS modules.

The completed project structure must include the root Terraform files, all three module directories, and `user_data.sh`:

```text
terraform-aws-epicbook/
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
└── modules/
    ├── network/
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── ec2/
    │   ├── main.tf
    │   ├── variables.tf
    │   ├── outputs.tf
    │   └── user_data.sh
    └── rds/
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```

## Evidence

### Screenshot 4 — Modular Project Structure

Add a screenshot of the VS Code Explorer showing the complete root project and the `network`, `ec2`, and `rds` module directory structure.

<img width="531" height="432" alt="Ass4-ss4" src="https://github.com/user-attachments/assets/57170f09-18dc-4892-b900-60ea32da5abc" />


---

# Task 2 — Build the Network Module

## Goal

Create a reusable Terraform network module containing the VPC, subnets, Internet Gateway, routing, and Security Groups required by EpicBook.

The network module must include:

- VPC: `10.0.0.0/16`
- Public subnet: `10.0.1.0/24`
- Private database subnet A: `10.0.2.0/24`
- Private database subnet B: `10.0.3.0/24`
- Private database subnets in different Availability Zones
- Internet Gateway
- Public route table and public-subnet association
- EC2 Security Group allowing SSH and HTTP
- RDS Security Group allowing MySQL port `3306` only from the EC2 Security Group
- Network module variables and outputs

## Evidence

### Screenshot 5 — VPC and Subnets

Add a screenshot of VS Code showing the VPC, public subnet, and two private database subnet configurations.

<img width="1296" height="653" alt="Ass4-ss5" src="https://github.com/user-attachments/assets/1b429606-10cd-40c2-af79-a9692b41667d" />


---

### Screenshot 6 — Internet Gateway and Public Routing

Add a screenshot of VS Code showing the Internet Gateway, public route table, and route table association.

<img width="1339" height="624" alt="Ass4-ss6" src="https://github.com/user-attachments/assets/391f2be9-c2dd-4a83-9e85-9df019915e0f" />


---

### Screenshot 7 — EC2 and RDS Security Groups

Add a screenshot of VS Code showing the EC2 and RDS Security Groups, including MySQL access from the EC2 Security Group only.

<img width="1355" height="603" alt="Ass4-ss7a" src="https://github.com/user-attachments/assets/1d87132d-e7e8-4c6b-a677-fd1deac3d8bb" />
<img width="1356" height="593" alt="Ass4-ss7b" src="https://github.com/user-attachments/assets/70aa3d06-4d77-47e3-a58f-65f624c8fbf7" />


---

### Screenshot 8 — Network Module Outputs

Add a screenshot of VS Code showing the network module outputs.

<img width="1359" height="491" alt="Ass4-ss8" src="https://github.com/user-attachments/assets/4fe746c7-ddb2-494b-b2f1-909c2df67c0c" />


---

# Task 3 — Build the EC2 Module and User Data Installation Script

## Goal

Create an EC2 module that launches the EpicBook application server inside the public subnet and automatically installs the required server software using EC2 user data.

The EC2 module must:

- Deploy the instance inside the public subnet
- Use the EC2 Security Group from the Network module
- Use a supported Ubuntu LTS AMI
- Assign a public IPv4 address
- Use an EC2 key pair for SSH authentication
- Connect `user_data.sh` through the EC2 `user_data` argument
- Expose the EC2 instance ID and public IP

The `user_data.sh` script must install the required software without storing database credentials or other secrets.

## Evidence

### Screenshot 9 — EC2 Resource and `user_data`

Add a screenshot of VS Code showing the EC2 resource and `user_data` configuration.

<img width="1353" height="673" alt="Ass4-ss9" src="https://github.com/user-attachments/assets/8fda4d6c-4021-4daa-8f51-9ca068c41ebc" />


---

### Screenshot 10 — `user_data.sh`

Add a screenshot of VS Code showing `user_data.sh`.

Ensure that no credentials, passwords, private keys, access tokens, or application secrets are visible.

<img width="1348" height="487" alt="Ass4-ss10" src="https://github.com/user-attachments/assets/24e33572-9c6f-4b26-a161-aa3f1ddbecfb" />


---

### Screenshot 11 — EC2 Module Variables and Outputs

Add a screenshot of VS Code showing the EC2 module variables and outputs.

<img width="1343" height="583" alt="Ass4-ss11a" src="https://github.com/user-attachments/assets/a609d9be-ee59-4a1b-b535-e37313afaeb3" />
<img width="1363" height="557" alt="Ass4-ss11b" src="https://github.com/user-attachments/assets/5581669d-ef31-4c4b-be73-e93fe43f0bc8" />


---

# Task 4 — Build the Amazon RDS Module

## Goal

Create an RDS module that provisions Amazon RDS for MySQL inside private database subnets.

The RDS module must include:

- A DB subnet group using both private database subnets
- Amazon RDS for MySQL
- RDS Security Group reference
- `publicly_accessible = false`
- Sensitive variables for database credentials
- RDS endpoint output
- No password output

## Evidence

### Screenshot 12 — DB Subnet Group and RDS MySQL

Add a screenshot of VS Code showing the DB subnet group and RDS MySQL configuration.

<img width="1349" height="379" alt="Ass4-ss12" src="https://github.com/user-attachments/assets/22912706-e09f-4637-b10e-dd5d88806916" />
<img width="976" height="376" alt="Ass4-ss12b" src="https://github.com/user-attachments/assets/a320bd83-125f-497e-addc-068974c9aec3" />


---

### Screenshot 13 — Private RDS and Sensitive Variables

Add a screenshot of VS Code showing `publicly_accessible = false`, the RDS Security Group configuration or reference, and the sensitive database variable configuration.

Ensure that the database password and other sensitive values are hidden.

<img width="1341" height="593" alt="Ass4-ss13" src="https://github.com/user-attachments/assets/adc362ce-22fa-40b1-9145-bf9de76b7ea8" />


---

### Screenshot 14 — RDS Endpoint Output

Add a screenshot of VS Code showing the RDS endpoint output.

<img width="1349" height="536" alt="Ass4-ss14" src="https://github.com/user-attachments/assets/1858d8ee-1830-4c7a-9cad-3bc36db97bb4" />


---

# Task 5 — Connect the Terraform Modules from the Root Module

## Goal

Use the root Terraform configuration to call the Network, EC2, and RDS modules and pass values between them.

## Evidence

### Screenshot 15 — Root Module Blocks

Add a screenshot of VS Code showing the root `main.tf` with the Network, EC2, and RDS module blocks.

<img width="331" height="138" alt="Ass4-ss15" src="https://github.com/user-attachments/assets/f740b144-1c7c-4108-9193-1f54c6be5a5d" />


---

### Screenshot 16 — Values Passed Between Modules

Add a screenshot of VS Code showing values passed from the Network module to the EC2 and RDS modules.



---

### Screenshot 17 — Root Outputs

Add a screenshot of VS Code showing the root EC2 public IP and RDS endpoint outputs.

<img width="1030" height="226" alt="Ass4-ss17" src="https://github.com/user-attachments/assets/270c9879-d5a7-4a4c-89f2-612aeb9024a7" />


---

# Task 6 — Initialize, Validate, Plan, and Apply the Terraform Configuration

## Goal

Initialize the modular Terraform project, validate the configuration, review the execution plan, and provision the AWS infrastructure.

## Evidence

### Screenshot 18 — Terraform Initialization

Add a screenshot of the terminal showing successful `terraform init` output.

<img width="787" height="328" alt="Ass4-ss18" src="https://github.com/user-attachments/assets/6f7ced0f-80d4-40be-bf5d-efc3fb367b09" />


---

### Screenshot 19 — Terraform Validation

Add a screenshot of the terminal showing successful `terraform validate` output.

<img width="480" height="115" alt="Ass4-ss19" src="https://github.com/user-attachments/assets/3f984378-ac68-479b-81ac-a2bc22a59b6c" />


---

### Screenshot 20 — Terraform Plan

Add a screenshot showing the Terraform plan summary and proposed resources.

<img width="1019" height="566" alt="Ass4-ss20" src="https://github.com/user-attachments/assets/5177c71c-8812-464f-bd36-255004fa23ea" />


---

### Screenshot 21 — Terraform Apply

Add a screenshot showing successful `terraform apply` completion.

<img width="1010" height="571" alt="Ass4-ss21" src="https://github.com/user-attachments/assets/247c47a9-517b-4287-be4d-280ce4b992e9" />


---

### Screenshot 22 — Terraform Outputs

Add a screenshot showing the EC2 public IP and RDS endpoint returned by `terraform output`.

<img width="779" height="230" alt="Ass4-ss22" src="https://github.com/user-attachments/assets/9092751e-c6a9-4176-8ab7-41b39e61d9e3" />


---

# Task 7 — Verify EC2, User Data, and Amazon RDS

## Goal

Verify that the EC2 and RDS resources were successfully provisioned and confirm that the EC2 user data script installed the required software.

## Evidence

### Screenshot 23 — EC2 Running

Add a screenshot of AWS CLI showing the EC2 instance running.

<img width="823" height="268" alt="Ass4-ss23" src="https://github.com/user-attachments/assets/7e919785-020b-4abf-9bb4-421a83afa8f7" />


---

### Screenshot 24 — Private RDS Available

Add a screenshot of AWS CLI showing that RDS is available and not publicly accessible.

<img width="793" height="235" alt="Ass4-ss24" src="https://github.com/user-attachments/assets/93ba04ae-008f-4b67-a6e7-0a3d9f4cc34e" />


---

### Screenshot 25 — Installed Software and Nginx

Add a screenshot of the EC2 terminal showing the required software version checks and the active Nginx service.

<img width="1086" height="330" alt="Ass4-ss25" src="https://github.com/user-attachments/assets/7c448165-2b64-4fef-a800-286a0cf12652" />


---

# Task 8 — Prepare the EpicBook Database

## Goal

Connect from EC2 to Amazon RDS, create the EpicBook database, import the schema and seed data, and verify the database contents.

## Evidence

### Screenshot 26 — EC2-to-RDS Connection

Add a screenshot of the terminal showing a successful connection from EC2 to Amazon RDS.

Ensure that the database password is not visible.

<img width="978" height="366" alt="Ass4-ss26" src="https://github.com/user-attachments/assets/57fdcbe8-0437-4aac-8a40-2c486bf0af2c" />


---

### Screenshot 27 — EpicBook Tables and Imported Data

Add a screenshot of the terminal showing the EpicBook tables and imported data.

<img width="1003" height="529" alt="Ass4-ss27a" src="https://github.com/user-attachments/assets/617c31e3-a03b-45b9-87e2-67cf0e3205af" />
<img width="1325" height="537" alt="Ass4-ss27b" src="https://github.com/user-attachments/assets/4fc83b79-9cbd-4b24-98ff-17177e407225" />


---

# Task 9 — Deploy and Configure the EpicBook Application

## Goal

Install EpicBook dependencies, configure the application to use Amazon RDS, configure Nginx as a reverse proxy, and start the application.

## Evidence

### Screenshot 28 — Dependencies and `node_modules`

Add a screenshot of the terminal showing successful dependency installation and the `node_modules` directory.

<img width="889" height="238" alt="Ass4-ss28" src="https://github.com/user-attachments/assets/9e3f4387-2e8c-4ffa-a067-4ada0495edf2" />


---

### Screenshot 29 — Nginx Configuration and Service

Add a screenshot of the terminal showing a successful Nginx configuration test and active service status.

<img width="679" height="157" alt="Ass4-ss29" src="https://github.com/user-attachments/assets/c9bc3154-ac13-4c5d-964c-bec4bc6351b8" />


---

### Screenshot 30 — EpicBook on Port `8080`

Add a screenshot of the terminal showing EpicBook running or listening on port `8080`.

<img width="1233" height="151" alt="Ass4-ss30" src="https://github.com/user-attachments/assets/01bc0d71-adf6-4f4b-ad11-1baeee43fb4c" />


---

# Task 10 — Test End-to-End Functionality

## Goal

Verify that EpicBook, EC2, Nginx, and Amazon RDS work together successfully.

## EC2 Public IP URL

**EC2 Public IP URL:** Add the working EpicBook EC2 public IP URL here

## Evidence

### Screenshot 31 — EpicBook Through the EC2 Public IP

Add a screenshot of the browser showing EpicBook using the EC2 public IP.

<img width="1343" height="704" alt="Ass4-ss31" src="https://github.com/user-attachments/assets/6330eca8-2ff7-45e5-8382-7abe7ed22d5f" />


---

### Screenshot 32 — Cart or Checkout Action

Add a screenshot of the browser showing a successful cart or checkout action.

<img width="1351" height="688" alt="Ass4-ss32" src="https://github.com/user-attachments/assets/79ef084c-0d76-436b-a542-be064bc2f448" />


---

### Screenshot 33 — Corresponding RDS Record

Add a screenshot of the terminal showing the corresponding RDS database record created by the application action.

Ensure that database credentials and other sensitive values are not visible.

<img width="649" height="320" alt="Ass4-ss33" src="https://github.com/user-attachments/assets/688be6d8-64cc-4afd-87ef-18e62a4fc98c" />


---

# Task 11 — Destroy the Terraform Infrastructure

## Goal

Remove all AWS resources created by the modular Terraform configuration.

## Evidence

### Screenshot 34 — Terraform Destroy

Add a screenshot of the terminal showing successful `terraform destroy` completion.

<img width="969" height="643" alt="Ass4-ss34" src="https://github.com/user-attachments/assets/cb64f45c-526c-4401-b9af-7d88435c72e6" />


---

# Task 12 — LinkedIn Post (Mandatory)

## Goal

Share what you built and learned from the modular AWS Terraform deployment.

Write the post in your own words and include at least one deployment screenshot or other proof. Ensure that the post can be viewed by the submission reviewer.

## Evidence

### Screenshot 35 — Published LinkedIn Post





## LinkedIn Post URL

**LinkedIn Post URL:**

---

# Submission Instructions

- Complete Tasks 0–12 in sequence.
- Include all Screenshots 1–35 exactly as specified.
- Ensure that your full name is visible in the required screenshots.
- Include the working EpicBook EC2 public IP URL.
- Include the published LinkedIn post URL.
- Include proof of frontend, backend, and database integration.
- Ensure that the required Terraform root files, module files, and `user_data.sh` are included in the GitHub submission.
- Do not upload Terraform state files, `.pem` files, or a `terraform.tfvars` file containing passwords or other sensitive values.
- Do not expose AWS credentials, account IDs, private SSH keys, RDS passwords, access tokens, Terraform sensitive values, or other confidential information.
- Review all screenshots and files carefully before submitting through GitHub.

---

# Completion Checklist

- [ ] Installed and verified Terraform
- [ ] Installed and verified AWS CLI
- [ ] Configured AWS CLI
- [ ] Confirmed the AWS Region
- [ ] Installed the HashiCorp Terraform extension
- [ ] Created the modular Terraform project
- [ ] Created the root `main.tf`, `variables.tf`, and `outputs.tf`
- [ ] Created the Network module
- [ ] Created the EC2 module
- [ ] Created the RDS module
- [ ] Created the EC2 `user_data.sh`
- [ ] Created VPC `10.0.0.0/16`
- [ ] Created public subnet `10.0.1.0/24`
- [ ] Created private DB subnet A `10.0.2.0/24`
- [ ] Created private DB subnet B `10.0.3.0/24`
- [ ] Used different Availability Zones for the database subnets
- [ ] Created and attached the Internet Gateway
- [ ] Created the public route table
- [ ] Associated the public subnet with the public route table
- [ ] Created the EC2 Security Group
- [ ] Allowed HTTP port `80`
- [ ] Restricted SSH port `22`
- [ ] Created the RDS Security Group
- [ ] Allowed MySQL port `3306` from the EC2 Security Group only
- [ ] Exposed the required Network module outputs
- [ ] Defined the EC2 instance
- [ ] Connected `user_data.sh` using the EC2 `user_data` argument
- [ ] Configured EC2 with a public IP
- [ ] Installed the required software using user data
- [ ] Created the RDS DB subnet group
- [ ] Created Amazon RDS for MySQL
- [ ] Confirmed RDS is not publicly accessible
- [ ] Configured sensitive database variables
- [ ] Exposed the RDS endpoint
- [ ] Connected all modules through the root module
- [ ] Passed Network module outputs to EC2 and RDS
- [ ] Added root EC2 public IP and RDS endpoint outputs
- [ ] Completed `terraform init`
- [ ] Completed `terraform validate`
- [ ] Reviewed `terraform plan`
- [ ] Completed `terraform apply`
- [ ] Verified EC2 is running
- [ ] Verified RDS is available
- [ ] Verified user data installation
- [ ] Connected to EC2 using SSH
- [ ] Cloned EpicBook
- [ ] Created the `bookstore` database
- [ ] Imported the database schema
- [ ] Imported author seed data
- [ ] Imported book seed data
- [ ] Verified database records
- [ ] Installed EpicBook dependencies
- [ ] Configured EpicBook to use RDS
- [ ] Configured Nginx
- [ ] Started EpicBook
- [ ] Verified port `8080`
- [ ] Loaded EpicBook through the EC2 public IP
- [ ] Verified product viewing
- [ ] Verified Add to Cart
- [ ] Verified the checkout or order workflow
- [ ] Confirmed application actions in Amazon RDS
- [ ] Completed `terraform destroy`
- [ ] Published the required LinkedIn post
- [ ] Added the LinkedIn post URL
- [ ] Captured all 35 required screenshots
- [ ] Confirmed that my full name is visible in the required screenshots
- [ ] Checked that no sensitive information is exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations through hands-on experience.

---

## Resources

- EpicBook Repository: [https://github.com/pravinmishraaws/theepicbook](https://github.com/pravinmishraaws/theepicbook)
- EpicBook Installation, Configuration & Troubleshooting Guide: [Installation & Configuration Guide](https://github.com/pravinmishraaws/theepicbook/blob/main/Installation%20%26%20Configuration%20Guide.md)
- DMI Official Website: [https://dmi.pravinmishra.com](https://dmi.pravinmishra.com)
- University: [https://university.pravinmishra.com](https://university.pravinmishra.com)
- Discord Community: [https://discord.pravinmishra.com](https://discord.pravinmishra.com)
- Blog: [https://dmi.pravinmishra.com/blog](https://dmi.pravinmishra.com/blog)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra on LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory on LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of the DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
