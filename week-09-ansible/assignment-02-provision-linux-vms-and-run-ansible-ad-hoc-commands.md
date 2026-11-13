# Assignment 02 — Provision Linux VMs with Terraform and Run Ansible Ad-Hoc Commands

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will use Terraform to provision three or four Ubuntu Linux Virtual Machines on either Microsoft Azure or Amazon Web Services.

You will configure SSH key-based authentication, organize the servers using a custom Ansible inventory, and run Ansible ad-hoc commands across individual hosts and inventory groups.

---

# Task 1 — Create the Multi-Host Lab Structure

## Goal

Create a separate project directory for the multi-host lab and prepare the Terraform, Ansible, and documentation files.

This project will use the Git repository and Ansible controller prepared in Assignment 01.

### Evidence

#### Screenshot 1 — Terminal showing the complete `ansible-adhoc-lab` project structure

<img width="879" height="380" alt="Ass2-ss1" src="https://github.com/user-attachments/assets/4325294b-aa9f-43c9-82e6-b89c94a74be7" />


---

#### Screenshot 2 — Terminal showing `git status --short` with the new project files and updated `.gitignore`

<img width="775" height="251" alt="Ass2-ss2" src="https://github.com/user-attachments/assets/2dd33e8d-0dd5-48ea-887e-0e03987f059b" />


---

### Notes



---

# Task 2 — Create the Terraform Configuration

## Goal

Create the Terraform configuration required to provision three or four Ubuntu Linux VMs on your selected cloud platform.

Complete only one option:

- Option A — Microsoft Azure
- Option B — Amazon Web Services

Do not configure both providers for this assignment.

### Evidence

#### Screenshot 3 — Terraform configuration showing the three or four server roles and the `for_each` or `count` implementation

<img width="985" height="498" alt="Ass2-ss3" src="https://github.com/user-attachments/assets/5c40cffc-ce2e-49cc-81e9-ca245863b350" />


---

#### Screenshot 4 — Terraform configuration showing SSH restricted to the controller IP and HTTP allowed only for web hosts

<img width="1366" height="709" alt="Ass2-ss4" src="https://github.com/user-attachments/assets/5f25a266-c14d-4ac6-9816-f0e69535245f" />


---

#### Screenshot 5 — Terraform output configuration showing how public IP addresses are associated with the server roles

<img width="1366" height="555" alt="Ass2-ss5" src="https://github.com/user-attachments/assets/6aaab7fb-b4ea-4dcb-9bb4-a11051e8580d" />


---

### Notes



---

# Task 3 — Provision the Infrastructure with Terraform

## Goal

Initialize and validate the Terraform configuration, review the execution plan, provision the selected three or four VMs, and retrieve their public IP addresses.

### Evidence

#### Screenshot 6 — Final `terraform apply` output showing `Apply complete`

<img width="1339" height="501" alt="Ass2-ss6" src="https://github.com/user-attachments/assets/b2bbd8ca-a192-466c-916e-ad021aa8dba2" />


---

#### Screenshot 7 — `terraform output public_ips` showing the role-to-IP mapping for all three or four VMs

<img width="1338" height="423" alt="Ass2-ss7" src="https://github.com/user-attachments/assets/90585ddf-1281-43fa-8b61-aa1791b8deb6" />


---

#### Screenshot 8 — Azure Portal or AWS Management Console showing all three or four VMs in the `Running` state, with their role-based names visible

<img width="1358" height="413" alt="Ass2-ss8" src="https://github.com/user-attachments/assets/22991971-7523-44de-b6cd-fb3886ba7fa2" />


---

### Notes



---

# Task 4 — Verify SSH Key-Based Access

## Goal

Verify that each managed VM can be accessed from the Ansible controller using SSH key-based authentication.

### Evidence

#### Screenshot 9 — Terminal showing successful SSH hostname output from all VMs

<img width="741" height="275" alt="Ass2-ss9" src="https://github.com/user-attachments/assets/698b1e01-ca05-4e5a-846a-e6355989e828" />


---

### Notes



---

# Task 5 — Create the Custom Ansible Inventory

## Goal

Create an Ansible inventory file that groups the managed VMs by role.

The inventory allows Ansible to run commands against all servers, or only specific groups such as `web`, `app`, or `db`.

### Evidence

#### Screenshot 10 — `inventory.ini` showing the `web`, `app`, and `db` groups

<img width="1272" height="381" alt="Ass2-ss10" src="https://github.com/user-attachments/assets/5b3d53e7-b2c9-4172-8694-bf9edc0d7e4c" />


---

#### Screenshot 11 — Output of `ansible-inventory -i inventory.ini --graph`

<img width="1160" height="263" alt="Ass2-ss11" src="https://github.com/user-attachments/assets/8817b293-6f0f-4c46-b23c-3ea0c9e410fa" />


---

### Notes




---

# Task 6 — Run Ansible Ad-Hoc Commands

## Goal

Run Ansible ad-hoc commands from the controller to verify connectivity, check server information, and manage packages and services across inventory groups.

This task proves that the inventory is working and that Ansible can control multiple managed VMs without writing a playbook.

### Evidence

#### Screenshot 12 — Output of `ansible all -i inventory.ini -m ping`

<img width="1069" height="475" alt="Ass2-ss12" src="https://github.com/user-attachments/assets/8eb60c6d-acc5-456d-adaa-b669595d648b" />


---

#### Screenshot 13 — Output of `ansible all -i inventory.ini -m command -a "uptime"`

<img width="1197" height="295" alt="Ass2-ss13" src="https://github.com/user-attachments/assets/8b451e0c-ccb2-4dd8-aa09-be6648c1fedf" />


---

#### Screenshot 14 — Output of `ansible web -i inventory.ini -m apt -a "name=nginx state=present update_cache=yes" --become`

<img width="1042" height="634" alt="Ass2-ss14" src="https://github.com/user-attachments/assets/f6cb9303-485f-444a-915f-8941e6f210a4" />


---

#### Screenshot 15 — Output of `ansible web -i inventory.ini -m service -a "name=nginx state=started enabled=yes" --become`

<img width="1043" height="626" alt="Ass2-ss15" src="https://github.com/user-attachments/assets/5ee14411-bd4e-4d28-80cb-a3e9f08d2663" />


---

#### Screenshot 16 — Output of `ansible all -i inventory.ini -m apt -a "name=htop state=present update_cache=yes" --become`

<img width="974" height="597" alt="Ass2-ss16" src="https://github.com/user-attachments/assets/a9121ea8-16b8-4567-b4fd-a4f6c5b63aeb" />


---

#### Screenshot 17 — Output of `ansible web -i inventory.ini -m command -a "systemctl is-active nginx"`

<img width="867" height="234" alt="Ass2-ss17" src="https://github.com/user-attachments/assets/8ee98bf3-e146-4425-8ab7-411bfd199c72" />


---

### Notes



---

# LinkedIn Post Required

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

#### Screenshot — Published LinkedIn post



---

# Assignment Questions

Answer the following in your own words:

**1. What is the purpose of an Ansible inventory file?**

The Ansible inventory file identifies the managed servers Ansible will control. It contains host information, connection details, and groups such as web, app, and db. This allows me to run commands against individual servers, specific groups, or all servers without listing their addresses every time.

---

**2. What is the difference between the `web`, `app`, and `db` groups in your inventory?**

web contains web servers that handle HTTP requests. In this lab, web1 and web2 run Nginx.

app contains application servers where application logic would run. In this lab, the server is app1.

db contains database servers intended to store and manage application data. In this lab, the server is db1.

---

**3. What does the Ansible `ping` module verify?**

The Ansible ping module checks whether Ansible can connect to a managed host over SSH and execute Python successfully. A successful result returns "ping": "pong". It is not the same as sending an ICMP network ping.

---

**4. Why do package installation commands require `--become`?**

The --become option enables privilege escalation, usually to the root user. Installing system packages, starting system services, and enabling services at boot generally require administrative privileges. Without --become, these operations may fail with permission errors.

---

**5. When would you use an ad-hoc command instead of a playbook?**

Ad-hoc commands are useful for quick, one-time tasks such as checking uptime, testing connectivity, installing a package, or checking service status. Playbooks are better for repeatable, multi-step automation that needs to be documented, version-controlled, reused, or shared across environments.

---

**6. What is one challenge you faced while setting up SSH or inventory, and how did you fix it?**

During this lab, SSH connections initially timed out because the AWS security group restricted SSH access to a specific IP address. I updated the security-group rule to allow SSH from other IPv4 addresses, which restored connectivity. I then used ANSIBLE_HOST_KEY_CHECKING=False temporarily for the Ansible commands to avoid interruptions from first-time SSH host-key prompts. After this, all four servers returned successful Ansible ping results.

---

# Required Files

The Terraform filenames below follow the recommended structure. An alternative organization is accepted if it meets the assignment requirements.

- [ ] `ansible-adhoc-lab/README.md`
- [ ] `ansible-adhoc-lab/terraform/providers.tf`
- [ ] `ansible-adhoc-lab/terraform/main.tf`
- [ ] `ansible-adhoc-lab/terraform/variables.tf`
- [ ] `ansible-adhoc-lab/terraform/outputs.tf`
- [ ] `ansible-adhoc-lab/ansible/inventory.ini`
- [ ] Updated `.gitignore`

---

# Submission Instructions

- Add all required screenshots from the tasks.
- Full Name must be visible in required screenshots.
- Mention whether you used Azure or AWS.
- Mention whether you used the three-VM option or four-VM option.
- Add the public IP addresses of the VMs, redacted if preferred.
- Add your `inventory.ini` proof.
- Add a short explanation of what you learned.
- Answer all assignment questions clearly in your own words.
- Add your LinkedIn post URL.
- Do not expose SSH private keys, Terraform state files, cloud credentials, passwords, access keys, secret keys, account IDs, or subscription IDs.

---

# Completion Checklist

- [ ] Task 1: `ansible-adhoc-lab` project structure created
- [ ] Task 1: `.gitignore` updated for Terraform files
- [ ] Task 2: Terraform configuration created
- [ ] Task 2: Server roles defined for either three or four VMs
- [ ] Task 2: `count` or `for_each` used
- [ ] Task 2: SSH restricted to the controller public IP
- [ ] Task 2: HTTP allowed only for web hosts
- [ ] Task 2: Terraform output maps roles to public IPs
- [ ] Task 3: Terraform initialized successfully
- [ ] Task 3: Terraform configuration validated
- [ ] Task 3: Terraform apply completed successfully
- [ ] Task 3: All selected VMs are running
- [ ] Task 4: SSH key-based access works for every VM
- [ ] Task 5: `inventory.ini` contains `web`, `app`, and `db` groups
- [ ] Task 5: `ansible-inventory -i inventory.ini --graph` shows the correct groups
- [ ] Task 6: `ansible all -i inventory.ini -m ping` returns `SUCCESS`
- [ ] Task 6: Ad-hoc commands run successfully
- [ ] Task 6: `--become` was used for package and service tasks
- [ ] Task 6: Nginx is active on the `web` group
- [ ] Screenshots 1–17 are included
- [ ] Assignment questions are answered
- [ ] LinkedIn post published
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
