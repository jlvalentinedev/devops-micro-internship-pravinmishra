# Assignment 04 — Deploy Mini Finance on Azure Using Terraform and Ansible

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will provision Azure infrastructure using Terraform and deploy the Mini Finance website using an Ansible multi-play playbook.

Terraform will create the Azure Virtual Machine and networking resources. Ansible will install Nginx, clone the Mini Finance repository, deploy the website, and verify the deployment.

---

# Task 1 — Create the Project Structure

## Goal

Create separate directories and files for the Terraform infrastructure and Ansible configuration.

### Evidence

#### Screenshot 1 — Terminal or VS Code showing the complete `mini-finance` project structure

<img width="686" height="346" alt="Ass4-ss1" src="https://github.com/user-attachments/assets/a3e534f9-81ce-4ac3-a2f4-9e7602652f50" />


---

### Notes



---

# Task 2 — Create the Azure Infrastructure Using Terraform

## Goal

Use Terraform to provision an Ubuntu Virtual Machine with the required Azure networking and security resources.

### Evidence

#### Screenshot 2 — Terraform code showing the `Allow-SSH` rule for port `22` and the `Allow-HTTP` rule for port `80`

<img width="723" height="597" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/90438cec-442b-4e82-ab72-e1b71a143981" />


---

#### Screenshot 3 — Terraform code showing the association between `nsg-mini-finance` and `nic-mini-finance`

<img width="1023" height="474" alt="Ass4-ss3" src="https://github.com/user-attachments/assets/89064628-ce41-448f-81b8-8a7b71569410" />


---

### Notes



---

# Task 3 — Initialize and Apply the Terraform Configuration

## Goal

Format and validate the Terraform configuration, review the execution plan, and provision the Azure infrastructure.

### Evidence

#### Screenshot 4 — End of the `terraform apply` output showing `Apply complete!` with no errors

<img width="806" height="228" alt="Ass4-ss4" src="https://github.com/user-attachments/assets/7f0d5783-ff47-49f6-a5b2-f01705c903fa" />


---

#### Screenshot 5 — Output of `terraform output public_ip` showing the VM’s public IP address

<img width="674" height="188" alt="Ass4-ss5" src="https://github.com/user-attachments/assets/40cd1cc9-cef4-4c14-bc0a-3256eb13bc0c" />


---

### Notes



---

# Task 4 — Verify Passwordless SSH Access

## Goal

Confirm that the Ansible controller can connect to the Terraform-provisioned Azure VM using SSH key authentication.

### Evidence

#### Screenshot 6 — Passwordless SSH command and the returned `mini-finance` hostname

<img width="607" height="219" alt="Ass4-ss6" src="https://github.com/user-attachments/assets/7bc00ae5-90e1-4de4-a825-f996f792ef5c" />


---

### Notes



---

# Task 5 — Create the Ansible Inventory and Verify Connectivity

## Goal

Add the Terraform-provisioned Azure VM to the Ansible inventory and confirm that Ansible can connect to it.

### Evidence

#### Screenshot 7 — Ansible ping output showing `SUCCESS` and `pong` from the Azure VM

<img width="929" height="332" alt="Ass4-ss7" src="https://github.com/user-attachments/assets/59235211-73b6-47e7-a086-92503b5b11a9" />


---

### Configuration File

Copy and paste the complete contents of your `ansible/inventory.ini` file below:

```ini

```

---

# Task 6 — Create the Multi-Play Ansible Playbook

## Goal

Create one Ansible playbook containing separate plays to install Nginx, deploy the Mini Finance website, and verify the deployment.

### Evidence

#### Screenshot 8 — `site.yml` showing Play 1 and the beginning of Play 2

Screenshot must show:

- Play 1 targeting the `web` group
- Installation of `nginx`, `git`, and `rsync`
- Nginx service configured as started and enabled
- Beginning of Play 2 with the Git repository URL and synchronization task

<img width="940" height="632" alt="Ass4-ss8" src="https://github.com/user-attachments/assets/6b2c0b52-3eb4-4ab2-b82a-6a4dd1d955c9" />


---

#### Screenshot 9 — `site.yml` showing the deployment destination, handler, and Play 3 verification

Screenshot must show:

- Website destination `/var/www/html/`
- Ownership set to `www-data:www-data`
- Nginx reload handler
- Play 3 targeting `localhost`
- The `uri` verification and `assert` condition

<img width="873" height="515" alt="Ass4-ss9" src="https://github.com/user-attachments/assets/009cd42b-740c-4704-8e20-0b63b1473287" />


---

### Configuration File

Copy and paste the complete contents of your `ansible/site.yml` file below:

```yaml

```

---

# Task 7 — Validate and Run the Ansible Playbook

## Goal

Validate the syntax of the multi-play Ansible playbook and run it to install Nginx, deploy the Mini Finance website, and verify the deployment.

### Evidence

#### Screenshot 10 — Successful playbook syntax check showing `playbook: site.yml`

<img width="1004" height="194" alt="Ass4-ss10" src="https://github.com/user-attachments/assets/c534fd43-1e62-4f69-adfb-0e90f11ba087" />


---

#### Screenshot 11 — Play 3 output showing the successful HTTP verification and assertion

<img width="1068" height="397" alt="Ass4-ss11" src="https://github.com/user-attachments/assets/a2d18076-f799-464a-b25c-369b2689d430" />


---

#### Screenshot 12 — Final `PLAY RECAP` showing `failed=0` and `unreachable=0`

<img width="1257" height="340" alt="Ass4-ss12" src="https://github.com/user-attachments/assets/706c95bb-a540-400e-bb10-4a8daabdfb27" />


---

### Notes



---

# Task 8 — Test the Mini Finance Website in a Browser

## Goal

Confirm that the Mini Finance website is publicly accessible through the Azure VM’s public IP address.

### Evidence

#### Screenshot 13 — Mini Finance website successfully loading in the browser, with the Azure VM’s public IP address visible in the address bar

<img width="1332" height="677" alt="Ass4-ss13" src="https://github.com/user-attachments/assets/ffce3210-0f8a-4d9e-beb6-6ba1f206497a" />


---

### Website URL

Add your deployed website URL below:

```text

```

---

# Task 9 — Create the Project README

## Goal

Create a `README.md` file to document the Mini Finance infrastructure and deployment project.

### Evidence

#### Screenshot 14 — Completed `README.md` displayed in the VS Code Markdown preview or terminal

<img width="1010" height="676" alt="Ass4-ss14a" src="https://github.com/user-attachments/assets/a54f6551-bc99-41f0-870f-da4cbe7b3bfe" />


---

### README Content

Copy and paste the complete contents of your `README.md` file below:

```markdown

```

---

# LinkedIn Post Required

## Evidence

#### Screenshot 15 — Published LinkedIn post showing the text and at least one deployment screenshot



---

#### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

### LinkedIn Submission Notes

**One challenge you faced and how you fixed it:**



---

**One real-world example where you can use this learning:**

I can use Terraform and Ansible together to deploy and manage a production website on AWS. Terraform can provision the required infrastructure, such as EC2 instances, security groups, and networking resources, while Ansible can install and configure Nginx, deploy website files, and verify that the website is accessible. This approach makes infrastructure provisioning and application deployment repeatable, consistent, and easier to maintain.

---

# Assignment Questions

Answer the following in your own words:

**1. What did you provision using Terraform in this assignment?**

I used Terraform to provision AWS infrastructure required for hosting the website, including an EC2 instance and a security group. The security group controls inbound traffic, allowing SSH access from my public IP address and HTTP traffic from the internet.

---

**2. What did Ansible configure and deploy in this assignment?**

Ansible installed and configured the required web server (Nginx), deployed the website files to the EC2 instance, and verified that the website was responding correctly.

---

**3. Why is SSH access on port `22` restricted to your public IP address?**

SSH access is restricted to my public IP address to reduce unauthorized access attempts. It ensures that only connections from my trusted network can remotely manage the EC2 instance, reducing its exposure to potential attackers.

---

**4. Why is HTTP port `80` open to the internet?**

HTTP port 80 is open to the internet so that users can access the hosted website through a web browser. Unlike SSH, which is used for administration, HTTP provides public access to the website.

---

**5. What is the purpose of the Ansible inventory file?**

The Ansible inventory file identifies the servers Ansible manages. It contains information such as the server's IP address, SSH username, connection details, and private key location, allowing Ansible to connect to the correct EC2 instance

---

**6. Why does the playbook use separate plays for install, deploy, and verify?**

Separating the playbook into installation, deployment, and verification makes the automation easier to understand, manage, and troubleshoot. Each play has a specific responsibility: installing dependencies, deploying website files, and checking that the website works correctly.

---

**7. Why is `rsync` useful when deploying website files?**

rsync transfers files efficiently by synchronizing changes between the local machine and the remote server. Instead of transferring every file repeatedly, it can transfer only changed files, saving time and bandwidth during deployment.

---

**8. What does the Ansible `uri` module verify in this assignment?**

The Ansible uri module sends an HTTP request to the deployed website and checks the response. It verifies that the web server is accessible and returns the expected HTTP status code, such as 200 OK.

---

**9. What issue did you face during this assignment, and how did you fix it?**

I encountered SSH connectivity and private key permission issues while connecting Ansible to the EC2 instance. I resolved the issue by copying the SSH private key into the appropriate location, setting the correct file permissions using chmod 600, and ensuring that the inventory file referenced the correct private key path.

---

**10. What did you learn from using Terraform and Ansible together?**

I learned that Terraform and Ansible complement each other in infrastructure automation. Terraform provisions the cloud infrastructure, while Ansible configures the servers and deploys applications. Using both tools creates a more repeatable and efficient deployment workflow, reduces manual configuration, and improves consistency.


---

# Required Files

Confirm that the following files are included in your assignment folder:

- [ ] `.gitignore`
- [ ] `README.md`
- [ ] `terraform/providers.tf`
- [ ] `terraform/main.tf`
- [ ] `terraform/variables.tf`
- [ ] `terraform/outputs.tf`
- [ ] `ansible/inventory.ini`
- [ ] `ansible/site.yml`

---

# Submission Instructions

- Add all required screenshots in the correct order.
- Full Name must be visible in required screenshots.
- Add the Azure VM public IP address.
- Add the final Mini Finance website URL.
- Paste `inventory.ini`, `site.yml`, and `README.md` as editable text.
- Answer all assignment questions clearly in your own words.
- Add your LinkedIn post URL.
- Do not expose SSH private keys, passwords, Azure credentials, subscription IDs, Terraform state contents, or other sensitive information.

---

# Completion Checklist

- [ ] Task 1: `mini-finance` project structure created
- [ ] Task 1: `.gitignore` created
- [ ] Task 2: Terraform Azure infrastructure code created
- [ ] Task 2: `Allow-SSH` rule configured for port `22`
- [ ] Task 2: `Allow-HTTP` rule configured for port `80`
- [ ] Task 2: NSG associated with the Network Interface
- [ ] Task 3: `terraform fmt` completed
- [ ] Task 3: `terraform init` completed
- [ ] Task 3: `terraform validate` completed successfully
- [ ] Task 3: `terraform apply` completed successfully
- [ ] Task 3: `terraform output public_ip` displayed the VM public IP
- [ ] Task 4: Passwordless SSH works from the Ansible controller
- [ ] Task 5: `inventory.ini` created
- [ ] Task 5: Ansible ping returns `SUCCESS` and `pong`
- [ ] Task 6: `site.yml` contains three separate plays
- [ ] Task 6: Play 1 installs Nginx, Git, and rsync
- [ ] Task 6: Play 2 clones and deploys the Mini Finance website
- [ ] Task 6: Play 3 verifies HTTP status code `200`
- [ ] Task 7: Playbook syntax check passes
- [ ] Task 7: Ansible playbook completes successfully
- [ ] Task 7: Final recap shows `failed=0` and `unreachable=0`
- [ ] Task 8: Mini Finance website loads in the browser
- [ ] Task 8: Azure VM public IP is visible in the browser screenshot
- [ ] Task 9: `README.md` completed
- [ ] Screenshots 1–15 are included
- [ ] `inventory.ini`, `site.yml`, and `README.md` are pasted as editable text
- [ ] Assignment questions are answered
- [ ] LinkedIn post published with Anyone visibility
- [ ] LinkedIn post URL added
- [ ] No sensitive information is exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra and The CloudAdvisory, focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## Resources

- DMI Official Website: [https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme](https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme)
- University: [https://university.pravinmishra.com?utm_source=github&utm_medium=readme](https://university.pravinmishra.com?utm_source=github&utm_medium=readme)
- Discord Community: [https://discord.pravinmishra.com?utm_source=github&utm_medium=readme](https://discord.pravinmishra.com?utm_source=github&utm_medium=readme)
- Blog: [https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme](https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
