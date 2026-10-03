# Assignment 6 — AI-Assisted Terraform Drift and Policy Review

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build a read-only Bash script that runs `terraform plan`, converts the plan to JSON, and checks it for two specific risks: resources that would be deleted or replaced, and any ingress or security rule that would open access to the whole internet. You will connect that script to Claude Code as a `/tf-drift-review` skill that explains what would change and whether `terraform apply` looks safe — without ever running `apply` or `destroy` itself. You will then deliberately introduce drift into your Terraform project, let the skill catch it, add a hook that blocks `apply` while a drift report is failing, and resolve the drift yourself.

---

# Task 1 — Confirm the Clean Baseline and Create the Workspace

## Goal

Confirm your existing Terraform project reports no pending changes, then create the folders for this assignment's script, skill, and reports.

### Evidence

#### Screenshot 1 — `terraform plan` showing no pending changes

<img width="1166" height="669" alt="Ass6-ss1" src="https://github.com/user-attachments/assets/a9122cda-d807-41d3-a769-05070dff9e04" />


---

#### Screenshot 2 — Folder structure showing the new workspace folders alongside your Terraform project

<img width="425" height="426" alt="Ass6-ss2" src="https://github.com/user-attachments/assets/acd1b987-5d8e-48d1-aa80-a39ca4261db9" />


---

# Task 2 — Create Project Context and Safety Rules in CLAUDE.md

## Goal

Add a `CLAUDE.md` describing the read-only drift-review workflow and the safety rules Claude must follow — never run `apply` or `destroy`, never use `-auto-approve`, only recommend a next step.

### Evidence

#### Screenshot 3 — `CLAUDE.md` open showing the project overview, review workflow, and safety rules

<img width="1344" height="686" alt="Ass6-ss3" src="https://github.com/user-attachments/assets/b509090c-ae30-418d-8347-3b67df65df76" />


---

# Task 3 — Build the Terraform Drift Check Script

## Goal

Create a Bash script that runs `terraform plan -detailed-exitcode`, converts the plan to JSON with `terraform show -json`, and uses `jq` to flag destructive resource changes and any ingress rule opening access to the whole internet.

### Evidence

#### Screenshot 4 — The script open showing its destructive-change and open-ingress checks

<img width="1072" height="651" alt="Ass6-ss4" src="https://github.com/user-attachments/assets/bf54e005-b126-4f6e-9647-f9bd30c01acd" />


---

#### Screenshot 5 — Terminal showing the script passes a syntax check and is executable

<img width="983" height="318" alt="Ass6-ss5" src="https://github.com/user-attachments/assets/5af85f21-3b32-4eb4-9d91-c2f6bf3db4c0" />


---

# Task 4 — Run the Script Against the Clean Baseline

## Goal

Run the script against your unchanged infrastructure and confirm it reports a healthy result with no destructive changes or open ingress found.

### Evidence

#### Screenshot 6 — Script output showing a healthy result against the clean baseline

<img width="715" height="196" alt="Ass6-ss6" src="https://github.com/user-attachments/assets/04094f32-c705-47b1-adbd-885c0cf2593a" />


---

# Task 5 — Create and Run the /tf-drift-review Skill

## Goal

Turn the script into a `/tf-drift-review` skill that reads the drift report, explains any risk in plain language, and states whether `apply` looks safe — restricted to read-only tools so it can never modify a file or run `apply`/`destroy` itself.

### Evidence

#### Screenshot 7 — Skill file showing the tool restrictions and safety rules

<img width="897" height="391" alt="Ass6-ss7" src="https://github.com/user-attachments/assets/fdb99067-bfd9-4d93-ac6b-bb79232eb98c" />


---

#### Screenshot 8 — `/tf-drift-review` output against the healthy baseline

<img width="648" height="263" alt="Ass6-ss8" src="https://github.com/user-attachments/assets/064c908b-68c5-4cd2-b532-1efe62f07a19" />


---

# Task 6 — Simulate Drift and Let the Skill Catch It

## Goal

Deliberately introduce a change Terraform did not make — a destructive change or a rule opening access to the whole internet — and confirm the skill flags it and does not run `apply` on its own.

### Evidence

#### Screenshot 9 — The drift you introduced, visible in your Terraform config or the cloud console

<img width="1355" height="634" alt="Ass6-ss9" src="https://github.com/user-attachments/assets/1bdb2d53-6f5c-48f4-8a83-ad537f4e98c3" />


---

#### Screenshot 10 — `/tf-drift-review` output flagging the drift and explaining the risk

<img width="1358" height="584" alt="Ass6-ss10" src="https://github.com/user-attachments/assets/1f50a4b4-7b54-416d-9926-da3106a1ed34" />


---

# Task 7 — Add a PreToolUse Hook That Blocks Apply on a Failed Report

## Goal

Extend the Week 2 hooks pattern with a `PreToolUse` hook that blocks any `terraform apply` command while the last drift report's status is failing.

### Evidence

#### Screenshot 11 — `settings.json` showing the new `PreToolUse` hook

<img width="1354" height="466" alt="Ass6-ss11" src="https://github.com/user-attachments/assets/d6b0b74e-41e2-43a5-a806-74c00ec368ee" />


---

#### Screenshot 12 — Claude's blocked response when attempting `terraform apply` while the report is failing

<img width="1337" height="565" alt="Ass6-ss12" src="https://github.com/user-attachments/assets/d0157a96-4e14-44e7-b6a6-bc8c353fc3b2" />


---

# Task 8 — Resolve the Drift, Verify, and Write the Review Summary

## Goal

Review the recommendation, resolve the drift yourself with a human-reviewed `terraform apply`, and confirm the hook no longer blocks it once the report is clean again.

### Evidence

#### Screenshot 13 — `terraform apply` completing successfully after your review

<img width="823" height="479" alt="Ass6-ss13" src="https://github.com/user-attachments/assets/9d4e5168-a407-4a4c-aa5c-468d4ab3c4eb" />


---

#### Screenshot 14 — Second `/tf-drift-review` run showing a healthy result

<img width="969" height="386" alt="Ass6-ss14" src="https://github.com/user-attachments/assets/72f56a5d-a09c-472f-91dd-e3c85a1b9d44" />


---

### Notes

Explain why this workflow needs both a fixed-rule hook that blocks `apply` outright and an AI skill that explains the risk in plain language — why isn't one of the two enough on its own?



---

# Submission Instructions

Complete all tasks in sequence.

Your submission must include:
- All 14 required screenshots

---

# Completion Checklist

- [ ] Task 1: Clean `terraform plan` baseline confirmed and workspace folders created (Screenshots 1–2)
- [ ] Task 2: `CLAUDE.md` created with project context and safety rules (Screenshot 3)
- [ ] Task 3: Drift check script built, passes syntax check, and is executable (Screenshots 4–5)
- [ ] Task 4: Script run against the clean baseline shows a healthy result (Screenshot 6)
- [ ] Task 5: `/tf-drift-review` skill created and run against the healthy baseline (Screenshots 7–8)
- [ ] Task 6: Drift simulated and correctly flagged by the skill (Screenshots 9–10)
- [ ] Task 7: `PreToolUse` hook created and shown blocking `apply` on a failing report (Screenshots 11–12)
- [ ] Task 8: Drift resolved with a human-reviewed `apply`, second review shows healthy (Screenshots 13–14)
- [ ] Notes question answered

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
