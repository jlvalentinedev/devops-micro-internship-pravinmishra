# Assignment 01 — Set Up a Team-Ready Ansible Development Workstation

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will prepare an isolated and reusable Ansible development workstation.

You will install Ansible and supporting tools inside a Python virtual environment, configure VS Code, prepare SSH access, configure Git and pre-commit hooks, and document the complete setup.

This workstation will be used as the Ansible controller in upcoming assignments.

---

# Task 1 — Create and Initialize the Ansible Workspace

## Goal

Create the assignment workspace, initialize a Git repository, prepare the required directories, and add Git ignore rules for local and sensitive files.

### Evidence

#### Screenshot 1 — Terminal showing the `ansible-onboarding` path, `ls -la` output, and `git status` confirming the Git repository is on the `main` branch

<img width="584" height="372" alt="Ass1-ss1" src="https://github.com/user-attachments/assets/18a1c5d2-3aca-4aab-8077-ce76011b506c" />


---

# Task 2 — Create the Virtual Environment and Install Ansible Tools

## Goal

Create an isolated Python virtual environment and install Ansible and the required validation tools without modifying the system Python environment.

### Evidence

#### Screenshot 2 — Terminal showing the active `(.venv)` environment, `which ansible`, `ansible --version`, `ansible-lint --version`, `yamllint --version`, and `pre-commit --version`

<img width="1039" height="222" alt="Ass1-ss2" src="https://github.com/user-attachments/assets/b1260df3-1020-4a21-a8b7-8f2b90972874" />
<img width="1130" height="361" alt="Ass1-ss2b" src="https://github.com/user-attachments/assets/3858605e-0949-45ed-afd6-a012fdf8c5d1" />


---

# Task 3 — Configure VS Code for Ansible Development

## Goal

Configure Visual Studio Code to use the project’s Python virtual environment and provide validation support for Python, YAML, and Ansible files.

### Evidence

#### Screenshot 3 — VS Code Extensions panel showing the Ansible, YAML, and Python extensions installed

<img width="1338" height="642" alt="Ass1-ss3" src="https://github.com/user-attachments/assets/aec5fc9d-d126-4a80-8148-acee714484d0" />


---

#### Screenshot 4 — VS Code showing `.vscode/settings.json` and `.editorconfig` open side by side, with the required settings clearly visible

<img width="1366" height="685" alt="Ass1-ss4" src="https://github.com/user-attachments/assets/eb07ad46-6a3c-4593-8500-be04684a96da" />


---

# Task 4 — Create the Baseline Ansible Configuration

## Goal

Create a reusable `ansible.cfg` file containing the default settings that will be used in this workspace and upcoming Ansible assignments.

### Evidence

#### Screenshot 5 — `ansible.cfg` open in VS Code or another editor, showing the complete configuration

<img width="1366" height="518" alt="Ass1-ss5" src="https://github.com/user-attachments/assets/e2a386b2-427b-4168-b068-79d678eb4670" />


---

#### Screenshot 6 — Terminal showing `ansible --version` with the `ansible.cfg` path and the output of `ansible-config dump --only-changed`

<img width="1025" height="485" alt="Ass1-ss6" src="https://github.com/user-attachments/assets/2a75d2eb-a6c3-4b6a-b46b-573c46bec96d" />


---

# Task 5 — Configure SSH Readiness

## Goal

Prepare SSH key authentication, load the key into the SSH agent, configure reusable SSH client settings, and understand how trusted host fingerprints are stored.

### Evidence

#### Screenshot 7 — Terminal showing `ssh-add -l` with the ED25519 key loaded and the SSH configuration verification output

<img width="970" height="244" alt="Ass1-ss7" src="https://github.com/user-attachments/assets/9b56f990-9319-4abe-91ac-599e0f851acb" />


---

# Task 6 — Configure Git Identity and Pre-commit Hooks

## Goal

Configure your Git identity and install pre-commit hooks that validate YAML and Ansible files before commits are created.

### Evidence

#### Screenshot 8 — Terminal showing your Git full name, Git email, default branch, successful `pre-commit install` output, and `.git/hooks/pre-commit`

<img width="1058" height="120" alt="Ass1-ss8" src="https://github.com/user-attachments/assets/5dd65b13-02b7-431c-9bf6-c63765f8ece7" />
<img width="1019" height="626" alt="Ass1-ss8b" src="https://github.com/user-attachments/assets/d310123a-2629-4132-96ce-496aabeb90e4" />


---

# Task 7 — Test the Complete Workstation Setup

## Goal

Verify that Ansible, the linting tools, Git hooks, SSH agent, and Git ignore rules are working correctly.

### Evidence

#### Screenshot 9 — Terminal showing `pre-commit run --all-files` completing successfully

<img width="850" height="177" alt="Ass1-ss9" src="https://github.com/user-attachments/assets/216b2275-a368-4917-a3aa-bbd5fb723a4b" />



---

#### Screenshot 10 — Terminal showing `ansible --version` with the project configuration path and `ssh-add -l` with the ED25519 key loaded

<img width="985" height="211" alt="Ass1-ss10" src="https://github.com/user-attachments/assets/489fe1ec-3445-43f7-a74b-42b5a51d869b" />
<img width="801" height="117" alt="Ass1-ss10b" src="https://github.com/user-attachments/assets/b9522f98-352c-4530-ab23-b33e6e772149" />


---

# Task 8 — Create the README and Onboarding Checklist

## Goal

Document the completed Ansible workstation setup and create a reusable checklist for preparing another workstation in the future.

### Evidence

#### Screenshot 11 — Terminal showing the final `ansible-onboarding` project structure

<img width="370" height="437" alt="Ass1-ss11" src="https://github.com/user-attachments/assets/d68a71f3-3ef6-4edb-b666-aff6d27e223f" />


---

#### Screenshot 12 — VS Code Markdown preview showing your full name, project summary, and part of the “New Machine? Do This” checklist



---

# Task 9 — Share Your Progress on WhatsApp

## Goal

Publish a WhatsApp Status showing a screenshot of your active Python virtual environment and Ansible version, a short caption about what you completed and learned, and your personal DMI progress link.

Get your progress link from **DMI Leaderboard → Your name → Share your progress**.

### Evidence

#### Screenshot 13 — Published WhatsApp Status showing your Ansible workstation screenshot, caption, and personal DMI progress link



> **Privacy Note:** Do not display private keys, credentials, private messages, phone numbers, or other sensitive information.

---

# Assignment Questions

Answer the following in your own words:

**1. What is one feature that makes your workstation setup team-friendly?**

Using a requirements.txt file makes the setup team-friendly because other team members can install the same Python dependencies and Ansible version, helping everyone maintain a consistent development environment.

---

**2. What is one pitfall you avoided while completing the setup?**

I avoided installing Ansible globally, which could cause dependency conflicts with other Python projects or system-managed packages. Instead, I used a dedicated virtual environment for the project.

---

**3. Why should Ansible be installed inside a Python virtual environment?**

A Python virtual environment isolates Ansible and its dependencies from the system Python installation. This prevents version conflicts, makes dependency management easier, and allows the project environment to be recreated consistently.

---

**4. Why must SSH private keys and `.venv/` remain outside version control?**

SSH private keys must remain outside version control because they contain sensitive credentials that could allow unauthorized access to servers. The .venv/ directory should also be excluded because it contains locally installed dependencies, can be recreated from the requirements file, and may differ across operating systems.

---

# Required Files

Confirm that the following files are included in your assignment workspace:

- [ ] `README.md`
- [ ] `requirements.txt`
- [ ] `.gitignore`
- [ ] `.editorconfig`
- [ ] `.vscode/settings.json`
- [ ] `ansible.cfg`
- [ ] `.pre-commit-config.yaml`
- [ ] `inventories/`
- [ ] `roles/`

---

# Submission Instructions

- Add all required screenshots in your submission.
- Full Name must be visible in required screenshots.
- All screenshots must be readable.
- Answer all assignment questions clearly in your own words.
- Do not expose SSH private-key contents, passwords, access tokens, API keys, credentials, private certificates, or other sensitive information.

---

# Completion Checklist

- [ ] Task 1: `ansible-onboarding` workspace created
- [ ] Task 1: Git initialized on the `main` branch
- [ ] Task 1: `.gitignore` created
- [ ] Task 2: Python virtual environment created
- [ ] Task 2: Virtual environment activated
- [ ] Task 2: Ansible installed inside `.venv`
- [ ] Task 2: `ansible-lint`, `yamllint`, and `pre-commit` installed
- [ ] Task 2: `requirements.txt` created
- [ ] Task 3: Required VS Code extensions installed
- [ ] Task 3: VS Code uses the Python interpreter from `.venv`
- [ ] Task 3: `.vscode/settings.json` created
- [ ] Task 3: `.editorconfig` created
- [ ] Task 4: `ansible.cfg` created
- [ ] Task 4: Ansible loads `ansible.cfg` from the project directory
- [ ] Task 5: ED25519 SSH key exists
- [ ] Task 5: SSH private key has not been exposed
- [ ] Task 5: SSH key loaded into the SSH agent
- [ ] Task 5: `~/.ssh/config` contains the required settings
- [ ] Task 5: `~/.ssh/known_hosts` exists
- [ ] Task 6: Git identity configured correctly
- [ ] Task 6: Pre-commit hooks installed
- [ ] Task 7: `pre-commit run --all-files` completes successfully
- [ ] Task 8: `README.md` contains your full name and workstation details
- [ ] Task 8: “New Machine? Do This” checklist contains 10–12 items
- [ ] Task 9: WhatsApp Status published with the workstation screenshot, caption, and DMI progress link
- [ ] All 13 required screenshots are included
- [ ] Assignment questions are answered
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
