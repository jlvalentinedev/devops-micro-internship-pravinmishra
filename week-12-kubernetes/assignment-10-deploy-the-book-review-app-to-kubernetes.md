# Assignment 10 — Capstone: Deploy the Book Review App to Kubernetes

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

Deploy the Book Review App as a production-style three-tier application using Kubernetes manifests or Helm charts, with an accessible frontend, an internal backend, and a managed or persistent MySQL database.

---

## Submission Details

**Full Name:** Add your full name here.

**Kubernetes Platform:** Add your platform here.

**Namespace:** book-review

**Frontend URL or IP:** Add the working endpoint here.

**Access Method:** Public LoadBalancer, Ingress, or documented local access.

**GitHub Manifests or Helm Chart URL:** Add your repository link here.

**Architecture Diagram:** Add your diagram or link here.

---

# Task 1 — Prepare the Kubernetes Cluster and Project

## Goal

Prepare the cluster, application source, container images, and tooling needed for the deployment.

### Evidence

#### Screenshot 1 — Active Kubernetes context and Ready nodes

<img width="1849" height="277" alt="image" src="https://github.com/user-attachments/assets/f4f4a0f8-1ecc-46e6-a8d6-f51d741a7f6b" />


---

#### Screenshot 2 — If using Helm: Output of `helm version`

Required only if you choose Helm. Skip this screenshot if using YAML manifests.

Not applicable — using YAML manifest

---

# Task 2 — Design the Three-Tier Kubernetes Architecture

## Goal

Document the workloads, networking, configuration, storage, and permitted communication paths before deployment.

### Evidence

#### Screenshot 3 — Completed Kubernetes architecture diagram

<img width="487" height="472" alt="image" src="https://github.com/user-attachments/assets/719f9673-07ad-4319-ad4e-881de0c98ff3" />


---

# Task 3 — Create ConfigMaps and Secrets

## Goal

Provide application configuration and credentials without embedding sensitive values in images or committing them to Git.

### Evidence

#### Screenshot 4 — ConfigMap configuration or describe output showing non-sensitive values

<img width="1036" height="448" alt="image" src="https://github.com/user-attachments/assets/cd019a2d-9f9c-4d27-8582-48a91eeb547a" />


---

#### Screenshot 5 — Secret references or describe output showing names and keys without sensitive values

<img width="1255" height="432" alt="image" src="https://github.com/user-attachments/assets/5cd2bddf-2958-4b55-858c-9ff68c43d715" />


---

# Task 4 — Deploy and Configure the MySQL Data Tier

## Goal

Provide persistent MySQL storage and allow the backend to connect without exposing the database publicly.

### Evidence

#### Screenshot 6 — Managed MySQL status or MySQL StatefulSet and PVC status

<img width="1807" height="301" alt="image" src="https://github.com/user-attachments/assets/55553ea5-91a8-40e4-a278-1e3431e4b74d" />


---

#### Screenshot 7 — Successful database connectivity or schema verification with credentials hidden

<img width="1132" height="504" alt="image" src="https://github.com/user-attachments/assets/faa7328a-3b3b-49aa-9aac-4343722116de" />


---

# Task 5 — Deploy the Backend Application Tier

## Goal

Run one or two Node.js/Express backend replicas on port 3001 and expose them through an internal ClusterIP Service.

### Evidence

#### Screenshot 8 — Backend Deployment, ready Pods, and internal Service

<img width="1273" height="391" alt="image" src="https://github.com/user-attachments/assets/79b611c8-699b-4f8b-ab45-54f9833985f1" />


---

#### Screenshot 9 — Backend startup logs and database connectivity evidence

If the application does not log successful database connections, provide a successful database-backed request alongside the startup logs.

<img width="1344" height="739" alt="image" src="https://github.com/user-attachments/assets/09e7b640-bece-4f2c-bb54-1dc717e8696e" />


---

# Task 6 — Deploy the Frontend and Configure Nginx

## Goal

Run the Next.js frontend behind Nginx on port 80 and proxy API requests to the internal backend Service.

### Evidence

#### Screenshot 10 — Frontend Deployment and Ready Pods

<img width="1230" height="568" alt="image" src="https://github.com/user-attachments/assets/b72b1c3a-0e86-4f49-940b-ca56fdd415fd" />


---

#### Screenshot 11 — Nginx reverse-proxy configuration showing the internal backend Service name and port 3001

<img width="1303" height="210" alt="image" src="https://github.com/user-attachments/assets/3fa70fd8-f8a6-4981-a200-bf5c9d429f3f" />


---

# Task 7 — Configure External and Internal Networking

## Goal

Expose the frontend and enforce the intended communication path between application tiers.

### Evidence

#### Screenshot 12 — Frontend LoadBalancer or Ingress configuration and assigned endpoint, or documented local access method

<img width="1774" height="331" alt="image" src="https://github.com/user-attachments/assets/a2cf2f14-9388-406a-8ce9-a4ee2857f6d1" />


---

#### Screenshot 13 — Internal backend Service and NetworkPolicy or equivalent restriction, with access-test evidence

<img width="1357" height="799" alt="image" src="https://github.com/user-attachments/assets/34d5df3c-8837-4870-b6f9-209e9b8251b0" />


---

# Task 8 — Validate the Application End to End

## Goal

Prove that the frontend, backend, and MySQL database work together and collect operational evidence.

### Evidence

#### Screenshot 14 — `kubectl get all` output for the book-review namespace

<img width="1357" height="799" alt="image" src="https://github.com/user-attachments/assets/34b04a44-1d5b-43ac-a01d-5ed9badcd7b0" />


---

#### Screenshot 15 — Functional Book Review App in the browser with the URL visible, including evidence of a successful user flow

<img width="1914" height="877" alt="image" src="https://github.com/user-attachments/assets/a229eb28-a0b2-4f85-b262-78e103f6df3c" />


---

#### Screenshot 16 — Frontend or Nginx container logs

<img width="1822" height="892" alt="image" src="https://github.com/user-attachments/assets/89e27caa-0696-4c32-bc59-cfbff5b3ee24" />


---

#### Screenshot 17 — Backend logs and evidence of a successful database-backed operation

<img width="1738" height="820" alt="image" src="https://github.com/user-attachments/assets/9de95f83-1670-4b71-8b09-5991d239e511" />


---

#### Screenshot 18 — Optional: Kubernetes dashboard



Multiple images may be included under a screenshot number when needed to demonstrate the complete user flow.

---

# Task 9 — Optional: Implement Production Improvements

## Goal

Add selected improvements without breaking the required three-tier architecture.

### Evidence

#### Screenshot 19 — Optional: Evidence of selected Helm, HPA, probe, or TLS improvements



---

# Task 10 — Publish Your Book Review App Deployment on LinkedIn

## Goal

Explain your three-tier architecture, demonstrate the working application, and share what you learned.

### Evidence

#### Screenshot 20 — Published LinkedIn post about your Book Review App deployment on Kubernetes



### LinkedIn Post URL



---

# Final Summary

## What Worked

Describe the application components and user flows you successfully deployed and tested.

I successfully deployed and tested NGINX applications using different Kubernetes Service types: ClusterIP, NodePort, and LoadBalancer on Azure Kubernetes Service (AKS).

I configured Deployments with multiple replicas, readiness probes, and liveness probes. I tested internal application communication using ClusterIP and DNS, explored external access through NodePort, and exposed an NGINX application publicly through an Azure LoadBalancer Service.

I also tested how Kubernetes handles Pod replacement, scaling, and readiness during rolling updates. I verified that Services provide stable access to applications even when backend Pods are replaced or scaled.

## Issues and Fixes

Describe the main issues encountered, their causes, and how you resolved them.

Describe the main issues encountered, their causes, and how you resolved them.

During the exercises, I intentionally introduced configuration errors to understand how Kubernetes responds to unhealthy workloads and incorrect Service configurations.

Readiness probe failures: An incorrect HTTP path caused Pods to become NotReady. I restored the correct probe path and reapplied the Deployment configuration.

Liveness probe failures: An invalid health-check path caused Kubernetes to restart unhealthy containers. I corrected the configuration to restore stable operation.

Service selector mismatch: An incorrect selector resulted in empty Service endpoints. I restored the matching Pod labels to re-establish connectivity.

NodePort connectivity: External access can depend on the cluster's networking configuration. I learned to distinguish between Service configuration issues and host-to-cluster network limitations.

LoadBalancer provisioning: The external IP may initially remain pending while Azure provisions the required networking resources. Waiting for the IP assignment allowed public endpoint testing.

## Tools and Sources Used

List the documentation and tools that helped you complete the assignment.

Tools and Sources Used
List the documentation and tools that helped you complete the assignment.

Tools:

Kubernetes (kubectl)

Azure Kubernetes Service (AKS)

Microsoft Azure Portal

NGINX

YAML manifests

Linux terminal / Ubuntu on WSL

Docker and Kubernetes container networking

curl for HTTP connectivity testing

## Optional Improvements

Describe any optional improvements implemented, or write “Not attempted.”



## Cleanup or Reuse Plan

State which resources were removed or why the environment is being retained.



---

# Submission Instructions

- Include your Kubernetes manifests or Helm chart in the linked repository.
- Submit Secret examples containing placeholders only.
- Include Screenshot 1, Screenshots 3–17, and Screenshot 20.
- Include Screenshot 2 only if using Helm.
- Screenshots 18–19 are optional.
- Keep screenshot numbering consistent with the guidelines.
- Use clear, readable screenshots showing relevant configuration, commands, and outputs.
- Make your full name visible in required screenshots.
- Complete the submission details and Final Summary.
- Include your published LinkedIn post URL.
- Capture required evidence before cleanup.
- Do not expose passwords, tokens, JWT secrets, actual Secret values, kubeconfig contents, cloud credentials, or confidential account information.

---

# Completion Checklist

- [ ] Selected and configured a supported Kubernetes platform
- [ ] Confirmed the context and Ready nodes (Screenshot 1)
- [ ] Created and selected the book-review namespace
- [ ] Inspected the application repository
- [ ] Prepared images accessible to the cluster
- [ ] Confirmed Helm if using charts (Screenshot 2, conditional)
- [ ] Created the architecture diagram (Screenshot 3)
- [ ] Created ConfigMaps and Secrets (Screenshots 4–5)
- [ ] Excluded actual Secret values from Git and screenshots
- [ ] Provisioned private managed MySQL or persistent Kubernetes MySQL (Screenshot 6)
- [ ] Initialized the required database and schema
- [ ] Verified database connectivity or schema (Screenshot 7)
- [ ] Deployed one or two backend replicas listening on port 3001
- [ ] Created the backend ClusterIP Service (Screenshot 8)
- [ ] Verified backend-to-database connectivity (Screenshot 9)
- [ ] Deployed one or two frontend replicas behind Nginx (Screenshot 10)
- [ ] Configured API proxying through the internal backend Service (Screenshot 11)
- [ ] Configured and documented frontend access (Screenshot 12)
- [ ] Enforced backend access restrictions (Screenshot 13)
- [ ] Confirmed that the backend and database are not publicly exposed
- [ ] Captured resource status for book-review (Screenshot 14)
- [ ] Tested application functionality and database writes (Screenshots 15 and 17)
- [ ] Verified saved data after application restart
- [ ] Captured frontend and backend logs (Screenshots 16–17)
- [ ] Included optional dashboard or improvement evidence if attempted (Screenshots 18–19)
- [ ] Published the LinkedIn post (Screenshot 20)
- [ ] Included the LinkedIn post URL
- [ ] Documented issues, fixes, and useful sources
- [ ] Recorded cleanup status or reuse plans
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

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
