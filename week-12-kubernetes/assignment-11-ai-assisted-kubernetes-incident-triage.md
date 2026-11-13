# Assignment 11 — AI-Assisted Kubernetes Incident Triage

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

Configure a read-only Bash triage script for your Book Review App, connect it to Claude Code through `/k8s-triage`, simulate one controlled failure, recover the application manually, and verify recovery.

**Workflow: Gather → Analyze → Human Act → Verify**

---

## Submission Details

**Full Name:** Add your full name here.

**Kubernetes Platform:** Add your platform here.

**Selected Workload:** Add the Deployment name here.

**Namespace:** Add the namespace here.

**GitHub Repository URL:** Add your project repository URL here.

**Simulated Incident:** Invalid image or broken readiness probe.

**Baseline Status:** HEALTHY or explained WARN.

**Recovery Status:** HEALTHY or explained WARN, with no FAIL.

---

# Task 1 — Discover the Application and Capture a Healthy Baseline

## Goal

Identify the actual application configuration and prove that the selected workload is healthy before incident simulation.

### Evidence

#### Screenshot 1 — Healthy Pods and ready Service backends

<img width="1816" height="789" alt="image" src="https://github.com/user-attachments/assets/4804ba08-78bb-4787-b45a-c852fdab9280" />


---

#### Screenshot 2 — Workspace directory structure

<img width="1552" height="259" alt="image" src="https://github.com/user-attachments/assets/c3ad40cb-779f-4ac3-a48d-b7b8a3dad782" />


### Notes

**1. What proves the selected Pods are ready, not merely running?**

The READY column shows that the expected containers are ready, for example 1/1. The Pod's Ready condition should also show True. A Pod showing Running alone does not prove that it is ready to receive traffic.

**2. What proves the Service has ready backends?**

The Service's EndpointSlices show the backend Pod IP addresses and their readiness conditions. A ready backend should have ready: true. The Service should also have at least one usable endpoint.

**3. Why must the original image be recorded before incident simulation?**

Recording the original image provides a known-good reference for recovery. It allows us to identify exactly what changed during the incident and restore the application to its previous working version.

---

# Task 2 — Configure CLAUDE.md

## Goal

Define the project configuration, incident workflow, and safety boundary for Claude Code.

### Evidence

#### Screenshot 3 — CLAUDE.md showing application configuration, workflow, safety rules, and output rules

<img width="1363" height="921" alt="image" src="https://github.com/user-attachments/assets/8a360a5a-58c6-4bd5-a682-8ffec954c02c" />


### Notes

**1. Why does Claude need project-specific cluster rules?**

Project-specific rules tell Claude which cluster, namespace, Deployment, Pod selector, and Service to investigate. They prevent it from making assumptions or examining unrelated workloads.

**2. Why must a human execute recovery commands?**

Human-controlled recovery prevents an AI agent from making unapproved changes to a Kubernetes environment. It ensures that a person reviews the diagnosis, understands the proposed action, and approves the change before execution.

**3. Which rule prevents an unsupported diagnosis?**

The evidence-based diagnosis rule. Claude must support every diagnosis with actual command output and collected evidence. It must report uncertainty instead of inventing a cause when the evidence is insufficient.

---

# Task 3 — Plan the Read-Only Triage Workflow

## Goal

Ask Claude Code to explain the five health checks before running the supplied script.

### Evidence

#### Screenshot 4 — Claude Code showing the five-check read-only plan

<img width="1860" height="961" alt="image" src="https://github.com/user-attachments/assets/7c844842-11e9-4a26-82ba-125c85228bc5" />


### Notes

**1. Which part represents the Gather phase?**

The Bash triage script performs the Gather phase by collecting Kubernetes evidence such as Pod status, readiness, container restarts, recent events, and Service backends.

**2. How did you verify that Claude did not change anything?**

I reviewed the planned commands and confirmed that the workflow used read-only Kubernetes inspection commands. No commands that modify, delete, restart, or redeploy Kubernetes resources were executed by Claude.

**3. Why is planning before coding useful for incident triage?**

Planning identifies the required health checks, defines the evidence to collect, and establishes safety boundaries before implementation. It makes the workflow more consistent, focused, and less likely to perform unintended actions.

---

# Task 4 — Configure and Validate the Bash Script

## Goal

Configure the supplied triage script for the selected workload and validate its syntax.

### Evidence

#### Screenshot 5 — Script configuration variables and checks array

<img width="1863" height="916" alt="image" src="https://github.com/user-attachments/assets/69dbb01d-9da3-49cc-b9f2-273b1da3fb91" />


---

#### Screenshot 6 — Functions for status, readiness, restarts, events, and Service backends

<img width="1824" height="247" alt="image" src="https://github.com/user-attachments/assets/9287e394-5b7d-4d7b-9e17-b9ad69d974b4" />


---

#### Screenshot 7 — Preflight, summary, and exit-code logic

<img width="1560" height="688" alt="image" src="https://github.com/user-attachments/assets/172f43ae-c8b0-40cb-af39-88a0d616aff0" />


---

#### Screenshot 8 — Successful syntax validation and executable permission

<img width="1006" height="235" alt="image" src="https://github.com/user-attachments/assets/4126b62d-12f1-4bbd-9a0a-17eba41dee3c" />


### Notes

**1. Why must the script fail when no Pods match the configured selector?**

If no Pods match the selector, the script cannot reliably assess the selected workload. Reporting a healthy status without finding the expected Pods could produce a misleading diagnosis.

**2. How does the readiness check detect a running but unready Pod?**

It checks the Pod's readiness condition or ready-container count rather than relying only on its Running phase. This allows the script to identify Pods that are running but not ready to receive traffic.

**3. Why are Service backends checked separately from Pod health?**

A Pod can be healthy while the Service selector is incorrect or its endpoints are missing. Checking Service backends separately confirms that healthy Pods are actually available to receive application traffic.

**4. What do exit codes 0, 1, and 2 represent?**

0 — All required checks passed; the workload is healthy.

1 — One or more health checks failed.

2 — A configuration, preflight, or execution error prevented reliable triage.

---

# Task 5 — Run the Healthy Baseline Report

## Goal

Run the script on the healthy application and confirm that it contains no failed checks.

### Evidence

#### Screenshot 9 — Baseline report showing your full name and all checks

<img width="1675" height="838" alt="image" src="https://github.com/user-attachments/assets/5629ed87-c33f-439b-b3d4-c19a33a4a023" />


---

#### Screenshot 10 — Captured exit code and final summary

<img width="1099" height="336" alt="image" src="https://github.com/user-attachments/assets/3f049ead-58f9-40f2-9c7c-d446cbc47378" />


### Notes

**1. What is the baseline status?**

HEALTHY — provided all required checks passed with no FAIL results.

**2. Which evidence proves the Service has a ready backend?**

The EndpointSlice output showing at least one backend Pod with ready: true proves that the Service has a ready endpoint.

**3. What is the difference between a warning and a failure?**

A warning identifies a condition that needs attention but does not necessarily mean the application is unavailable. A failure indicates that a required health check did not pass and may affect application availability or reliability.

---

# Task 6 — Configure and Run the Claude Code Skill

## Goal

Connect the Bash script to a manually invoked Claude Code evidence-analysis workflow.

### Evidence

#### Screenshot 11 — SKILL.md showing frontmatter and safety rules

<img width="1726" height="871" alt="image" src="https://github.com/user-attachments/assets/d61697ad-d58a-479f-9255-79901bc60628" />


---

#### Screenshot 12 — Baseline `/k8s-triage` analysis

<img width="1861" height="811" alt="image" src="https://github.com/user-attachments/assets/f68d7a6a-cb6b-468d-9472-038f364d593d" />


### Notes

**1. What does Bash do in this workflow?**

Bash executes the read-only triage script, collects Kubernetes health evidence, evaluates the checks, and generates a report.

**2. What does Claude do in this workflow?**

Claude analyzes the evidence collected by Bash, identifies the most likely supported cause of an incident, explains the findings, and suggests a manual recovery action for human review.

**3. Why are instructions alone insufficient to guarantee read-only access?**

Instructions guide the AI agent but do not technically prevent it from executing commands that change resources. The workflow must also enforce safety through script design, restricted command execution, and human approval of recovery actions.

---

# Task 7 — Simulate One Controlled Incident

## Goal

Create one controlled failure, save its evidence, and let Claude analyze it without executing recovery.

### Evidence

#### Screenshot 13 — Failed or unready Pod evidence and current Service backends

<img width="1852" height="310" alt="image" src="https://github.com/user-attachments/assets/6c199275-472d-4acf-8684-6c4dd031fcf8" />


---

#### Screenshot 14 — Failed `/k8s-triage` analysis with evidence and a suggested manual recovery command

<img width="1882" height="627" alt="image" src="https://github.com/user-attachments/assets/8c22f7be-b25b-4e67-bda3-3fff56be02a9" />


---

#### Screenshot 15 — Saved `incident-failure-report.txt`

<img width="1198" height="294" alt="image" src="https://github.com/user-attachments/assets/e007b9df-bd67-4cca-a8a3-229b75129f31" />


### Notes

**1. Which failure did you choose?**

Invalid image: I intentionally changed the container image to an invalid or unavailable image to simulate an image-pull failure.

Broken readiness probe: I intentionally configured an incorrect readiness-probe path to simulate an application that runs but cannot become ready.

**2. Which checks failed, and what evidence proved it?**

For an invalid image: The Pod health or container-status check reported a problem. Evidence such as ErrImagePull or ImagePullBackOff confirmed that Kubernetes could not retrieve the configured image.

For a broken readiness probe: The readiness check failed because the container did not pass its configured HTTP health check. The Pod showed Ready: False, and probe failure events provided supporting evidence.

**3. Did Claude execute recovery? Why is that important?**

No. Claude only collected or analyzed evidence and suggested a recovery action. Recovery was performed manually to preserve human control, prevent unauthorized changes, and ensure that the proposed fix was reviewed before execution.

**4. Why might the Service retain ready backends during the incident?**

The Service may still have other healthy Pods that match its selector. Kubernetes excludes unready Pods from ready Service backends while continuing to route traffic to the remaining ready Pods.

---

# Task 8 — Recover Manually and Verify

## Goal

Restore the healthy configuration yourself and verify recovery using a second triage report.

### Evidence

#### Screenshot 16 — Recovered Pods and ready Service backends

<img width="1848" height="807" alt="image" src="https://github.com/user-attachments/assets/1ef52cf5-90c9-48a3-a2ab-6de972e4a77e" />


---

#### Screenshot 17 — Recovered `/k8s-triage` analysis

<img width="1867" height="720" alt="image" src="https://github.com/user-attachments/assets/6a830cc0-cacf-417c-8c63-102f99aeda68" />


---

#### Screenshot 18 — Reports directory showing failure and recovery reports

<img width="1123" height="384" alt="image" src="https://github.com/user-attachments/assets/8b62c9d5-a65d-4c34-8a50-d5f5ae3004c8" />


---

#### Screenshot 19 — `incident-summary.md` with all required sections

<img width="1858" height="919" alt="image" src="https://github.com/user-attachments/assets/79a7e4cf-28d8-488d-8455-24e6ae121114" />


### Notes

**1. What manual recovery action did you execute?**

For an invalid image: I manually restored the original working container image in the Deployment and applied the corrected configuration.

For a broken readiness probe: I manually restored the correct readiness-probe configuration and applied the updated Deployment.

**2. What proves the workload recovered?**

The recovered Pods reached Running and Ready status, the expected replica count became available, the Service EndpointSlices showed ready backends, and the recovery triage report contained no FAIL results.

**3. Why is the second triage run necessary?**

The second triage run independently verifies the application after manual recovery. It provides evidence that the original problem has been resolved and that the workload and Service backends have returned to a healthy state.

**4. Why should AI not automatically restart every failing production workload?**

Not every failure is caused by a problem that restarting can fix. Automatic restarts could cause service disruption, destroy useful diagnostic evidence, worsen an incident, or hide the underlying problem. Human review helps ensure that recovery actions are appropriate and safe.

### Remaining WARN Results

Explain any WARN results remaining after recovery, or write “None.”



---

# Task 9 — Publish Your Kubernetes Incident-Triage Workflow on LinkedIn

## Goal

Share the incident-triage workflow you completed and explain the role of human control.

### Evidence

#### Screenshot 20 — Published LinkedIn post about your Kubernetes incident-triage workflow



### LinkedIn Post URL



---

# Required Project Files

Include these files in your project repository:

- `CLAUDE.md`
- `lab-config.md`
- `scripts/k8s-triage.sh`
- `.claude/skills/k8s-triage/SKILL.md`
- `reports/incident-failure-report.txt`
- `reports/recovery-report.txt`
- `incident-summary.md`

Your `incident-summary.md` must contain:

1. Reported Symptom
2. Evidence Collected
3. Most Likely Cause
4. Human-Approved Recovery Action
5. Verification
6. Safety Decision
7. Agentic Loop Mapping

---

# Final Summary

## Evidence and Cause

Summarize the evidence and the supported cause of the incident.

Add your summary here.

## Manual Recovery

Describe the command or configuration change you performed.

Add your summary here.

## Verification

Explain how the recovery report and Kubernetes outputs confirmed recovery.

Add your summary here.

## Safety Decision

Explain how you kept Claude’s role limited to evidence gathering and analysis.

Add your summary here.

---

# Submission Instructions

- Include all 20 required screenshots under their corresponding Evidence sections.
- Complete all Notes questions in your own words.
- Include the required project files in your linked repository.
- Include your published LinkedIn post URL.
- Use clear, readable screenshots showing relevant commands, configuration, and outputs.
- Display your full name before taking required terminal screenshots.
- Preserve the failure report before recovery.
- Ensure the baseline and recovery reports contain no FAIL results.
- Explain any WARN results remaining after recovery.
- Review reports, logs, configuration records, and screenshots before publishing.
- Do not expose credentials, kubeconfig contents, tokens, certificates, JWT secrets, or confidential account information.

---

# Completion Checklist

- [ ] Confirmed the personal lab context
- [ ] Discovered and recorded application configuration
- [ ] Recorded the original working image
- [ ] Captured healthy Pods and ready Service backends (Screenshot 1)
- [ ] Created the workspace (Screenshot 2)
- [ ] Configured CLAUDE.md (Screenshot 3)
- [ ] Reviewed the five-check triage plan (Screenshot 4)
- [ ] Configured and reviewed the supplied script (Screenshots 5–7)
- [ ] Passed Bash syntax validation and set executable permission (Screenshot 8)
- [ ] Captured a baseline report with no FAIL (Screenshot 9)
- [ ] Captured the correct exit code (Screenshot 10)
- [ ] Configured and invoked `/k8s-triage` (Screenshots 11–12)
- [ ] Simulated one controlled incident manually (Screenshot 13)
- [ ] Reviewed Claude’s failed-state analysis (Screenshot 14)
- [ ] Saved failure evidence before recovery (Screenshot 15)
- [ ] Executed recovery manually and waited for rollout completion
- [ ] Confirmed recovered Pods and ready Service backends (Screenshot 16)
- [ ] Captured recovery analysis with no FAIL (Screenshot 17)
- [ ] Explained any remaining warnings
- [ ] Saved failure and recovery reports (Screenshot 18)
- [ ] Completed the seven-section incident summary (Screenshot 19)
- [ ] Answered all Notes questions
- [ ] Published the LinkedIn post (Screenshot 20)
- [ ] Included the LinkedIn post URL
- [ ] Included all required project files
- [ ] Checked that no sensitive information is exposed

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

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
