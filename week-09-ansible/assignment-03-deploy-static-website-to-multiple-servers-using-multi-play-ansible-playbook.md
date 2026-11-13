# Assignment 03 — Deploy a Static Website to Multiple Servers Using a Multi-Play Ansible Playbook

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Student Details

**Full Name:** Add your full name here  
**Cloud Platform Used:** AWS / Azure  
**Server 1 URL:** `http://<SERVER_1_PUBLIC_IP>`  
**Server 2 URL:** `http://<SERVER_2_PUBLIC_IP>`

---

## Purpose

In this assignment, you will create a multi-play Ansible playbook to install Nginx, deploy a static website to two Ubuntu servers, and verify that the website is accessible from both servers.

You may use either AWS EC2 instances or Azure Virtual Machines as your managed servers.

---

# Task 1 — Create the Project Structure

## Goal

Create the required folders and files for the Ansible project.

## Evidence

### Screenshot 1 — Terminal or VS Code showing the complete `static-web` project structure

<img width="1068" height="197" alt="Ass3-ss1" src="https://github.com/user-attachments/assets/caa3522c-dcc0-42c5-b4a7-12cd56b30c6c" />


---

# Task 2 — Configure the Ansible Inventory

## Goal

Add both Ubuntu servers to the Ansible inventory.

## Evidence

### Screenshot 2 — Output of `ansible-inventory -i inventory.ini --graph` showing `web1` and `web2`

<img width="1112" height="252" alt="Ass3-ss2" src="https://github.com/user-attachments/assets/82cebc5a-35a0-47c1-9ce9-1be8e73df2b6" />


---

## Configuration File

Copy and paste the complete contents of your `inventory.ini` file below:

```ini
Add your inventory.ini content here.
```

---

# Task 3 — Verify Ansible Connectivity

## Goal

Confirm that the Ansible controller can connect to both servers.

## Evidence

### Screenshot 3 — Ansible ping output showing `SUCCESS` and `pong` for both servers

<img width="1283" height="344" alt="Ass3-ss3" src="https://github.com/user-attachments/assets/7ac67507-f014-4a74-b0d7-dbffd0bcfb01" />


---

# Task 4 — Download and Personalize the Static Website

## Goal

Download `index.html` to the Ansible controller and personalize the website with your full name.

## Evidence

### Screenshot 4 — Edited `files/index.html` showing the footer line with your full name

<img width="1105" height="162" alt="Ass3-ss4" src="https://github.com/user-attachments/assets/c54b1976-8b2a-4c5b-881f-1488a7c3bc9d" />


---

# Task 5 — Create the Multi-Play Ansible Playbook

## Goal

Create a single Ansible playbook containing separate plays for installation, deployment, and verification.

## Configuration File

Copy and paste the complete contents of your `site.yml` file below:

```yaml
Add your site.yml content here.
```

---

# Task 6 — Validate the Playbook Syntax

## Goal

Check the playbook for YAML or Ansible syntax errors before running it.

## Evidence

### Screenshot 5 — Successful syntax-check output showing `playbook: site.yml`

<img width="1272" height="222" alt="Ass3-ss5" src="https://github.com/user-attachments/assets/9b9e4669-c65e-470a-acb4-01ab8dacefea" />


---

# Task 7 — Run the Multi-Play Playbook

## Goal

Install Nginx, deploy the website, and verify both servers in one playbook run.

## Evidence

### Screenshot 6 — Play 3 verification showing HTTP `200` for both servers

<img width="991" height="462" alt="Ass3-ss6" src="https://github.com/user-attachments/assets/3318f56f-fe23-49a3-96c9-dacad37e8b00" />


---

### Screenshot 7 — Final play recap showing `unreachable=0` and `failed=0` for `web1`, `web2`, and `localhost`

<img width="1128" height="365" alt="Ass3-ss7" src="https://github.com/user-attachments/assets/5c4aaa9e-c3f4-458a-9fbd-4ffec8d70f0f" />


---

# Task 8 — Verify Idempotency

## Goal

Run the playbook again and confirm that it does not make unnecessary changes.

## Evidence

### Screenshot 8 — Second playbook run showing the play recap with `changed=0`, `unreachable=0`, and `failed=0` for both web servers

<img width="1124" height="381" alt="Ass3-ss8" src="https://github.com/user-attachments/assets/f81976ce-847f-4814-a21a-a247e7eaca06" />


---

# Task 9 — Test Both Websites Manually

## Goal

Confirm that the static website is accessible from both public IP addresses.

## Evidence

### Screenshot 9 — `curl -I` output showing HTTP `200 OK` from both servers

<img width="1020" height="482" alt="Ass3-ss9" src="https://github.com/user-attachments/assets/71f98ef5-bafb-4e5f-861e-bbb2e7289c2d" />


---

### Screenshot 10 — Browser showing the website from Server 1 with the public IP and your full name visible

<img width="1366" height="714" alt="Ass3-ss10" src="https://github.com/user-attachments/assets/db3644f1-8893-49ad-840e-c77640c96411" />


---

### Screenshot 11 — Browser showing the website from Server 2 with the public IP and your full name visible

<img width="1366" height="745" alt="Ass3-ss11a" src="https://github.com/user-attachments/assets/f8aa4619-4fc1-4e26-a53a-563f3acdad51" />
<img width="1366" height="701" alt="Ass3-ss11b" src="https://github.com/user-attachments/assets/12fdc46f-04cb-46ca-a076-10357c29e528" />


---

## Website URLs

Add both deployed website URLs below:

```text
Server 1: http://<SERVER_1_PUBLIC_IP>
Server 2: http://<SERVER_2_PUBLIC_IP>
```

---

# Task 10 — Complete the Project README

## Goal

Document how the project works and record what you learned.

## README Content

Copy and paste the complete contents of your `README.md` file below:

```markdown

```

---

# LinkedIn Post Required

## Evidence

### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

### Screenshot — Published LinkedIn post



---

# Assignment Questions

Answer the following in your own words:

**1. What issue did you face while completing this assignment, and how did you fix it?**

The main issue I faced was an SSH connection timeout when Ansible tried to connect to both EC2 web servers. I discovered that the security group allowed SSH access only from an outdated public IP address. I fixed this by updating the inbound SSH rule to allow my current public IP address, after which Ansible successfully pinged both servers.

---

**2. What did you learn from this assignment?**

I learned how to use a multi-play Ansible playbook to automate the deployment of a static website to multiple AWS EC2 servers. I also learned how to configure an inventory, install and manage Nginx, copy website files, use handlers, verify HTTP responses, and test idempotency.

---

**3. Why is it useful to split installation, deployment, and verification into separate plays?**

Splitting these tasks into separate plays makes the playbook easier to understand, maintain, and troubleshoot. Each play has a specific responsibility: installing and configuring Nginx, deploying the website, or verifying that the servers respond correctly. It also allows verification to run from the Ansible controller without requiring administrative privileges on localhost.

---

**4. What is one benefit of using the Ansible `copy` module instead of cloning the website directly from Git on every managed server?**

The copy module allows me to maintain one version of the website file on the Ansible controller and distribute the same file to all managed servers. This keeps the deployment consistent and avoids requiring Git or repository access on every web server.

---

**5. What does idempotency mean in this assignment?**

Idempotency means that running the same playbook repeatedly produces the desired state without making unnecessary changes. In this assignment, the second run reported changed=0 on both web servers because Nginx was already installed and running, and the website files were already up to date.

---

**6. What does the Ansible `uri` module verify in Play 3?**

The uri module sends HTTP requests to both web servers and checks their responses. In this assignment, it verifies that each website returns HTTP status code 200, confirming that the web pages are accessible and responding successfully.

---

# Required Files

Confirm that the following files are included in your assignment folder:

- [ ] `inventory.ini`
- [ ] `site.yml`
- [ ] `files/index.html`
- [ ] `README.md`

---

# Submission Instructions

- Add all required screenshots in the correct order.
- Full Name must be visible in required screenshots.
- Include both deployed website URLs.
- Paste `inventory.ini`, `site.yml`, and `README.md` as editable text.
- Answer all assignment questions clearly in your own words.
- Add your LinkedIn post URL.
- Do not expose SSH private keys, passwords, cloud account IDs, or other sensitive information.

---

# Completion Checklist

- [ ] Task 1: `static-web` folder structure is complete
- [ ] Task 2: Both servers are listed under the `[web]` group in `inventory.ini`
- [ ] Task 2: Inventory graph shows `web1` and `web2`
- [ ] Task 3: Ansible ping returns `SUCCESS` and `pong` for both servers
- [ ] Task 4: `files/index.html` contains your full name
- [ ] Task 5: `site.yml` contains three separate plays
- [ ] Task 5: Play 1 installs, starts, and enables Nginx
- [ ] Task 5: Play 2 deploys `index.html` using the `copy` module
- [ ] Task 5: Nginx reload handler is included
- [ ] Task 5: Play 3 verifies both web servers from the controller
- [ ] Task 6: Playbook syntax check passes
- [ ] Task 7: First playbook run completes with `unreachable=0` and `failed=0`
- [ ] Task 7: URI verification returns HTTP `200` for both servers
- [ ] Task 8: Second playbook run demonstrates idempotency
- [ ] Task 8: Second run shows `changed=0` for both web servers
- [ ] Task 9: Both `curl -I` commands return HTTP `200 OK`
- [ ] Task 9: Website loads from Server 1
- [ ] Task 9: Website loads from Server 2
- [ ] Task 9: Full name is visible on both deployed websites
- [ ] Task 10: `README.md` contains all required explanations
- [ ] Screenshots 1–11 are included
- [ ] `inventory.ini`, `site.yml`, and `README.md` are pasted as editable text
- [ ] Both website URLs are included
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
