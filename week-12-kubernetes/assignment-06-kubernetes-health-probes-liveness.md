# Assignment 6 — Kubernetes Health Probes (Liveness)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will configure and test a Kubernetes liveness probe. You will create a baseline NGINX Deployment, add an HTTP liveness probe, intentionally make it fail, observe container restarts, and restore the working configuration.

---

# Task 0 — Prepare the Lab Environment

## Goal

Confirm that you are connected to your learning cluster and remove the previous HPA and NGINX Deployment before starting this lab.

No screenshot or written notes are required for this pre-check.

---

# Task 1 — Set Up Your Lab Directory

## Goal

Create and enter a dedicated directory for the liveness-probe lab.

### Evidence

#### Screenshot 1 — Terminal showing that you are working inside `~/k8s-labs/health-probes-liveness`

<img width="1188" height="262" alt="image" src="https://github.com/user-attachments/assets/e8f02977-6a9c-4843-ad58-7eb16890fbff" />


---

### Notes

**1. What problem does a liveness probe solve?**

A liveness probe detects when a container is unhealthy or stuck and unable to function correctly. Kubernetes can restart the container automatically to recover it.

**2. What is the key difference between a readiness probe and a liveness probe?**

A readiness probe determines whether a Pod is ready to receive traffic, while a liveness probe determines whether a container is healthy enough to keep running. Failed readiness checks stop traffic from being sent to the Pod, while repeated liveness failures cause Kubernetes to restart the container.

---

# Task 2 — Create a Baseline Deployment Without Probes

## Goal

Create a baseline NGINX Deployment with two replicas and no health probes.

### Evidence

#### Screenshot 2 — Completed `00-nginx-deploy-baseline.yaml` manifest

<img width="1126" height="739" alt="image" src="https://github.com/user-attachments/assets/f2dca03b-e397-43e2-a464-bd76276f14d0" />


---

#### Screenshot 3 — Output showing a successful rollout and two running NGINX Pods

<img width="1701" height="378" alt="image" src="https://github.com/user-attachments/assets/f4bf0b32-4b9f-4d76-8104-e0b2b3bb0d91" />


---

#### Screenshot 4 — Relevant output from `kubectl describe deployment nginx-deployment`

<img width="1419" height="682" alt="image" src="https://github.com/user-attachments/assets/2be25547-7711-4b64-82ea-c79152700d30" />


---

### Notes

**1. How many replicas does this Deployment maintain?**

The Deployment maintains two NGINX Pod replicas.

**2. Are any health probes configured in the baseline Deployment?**

No. The baseline Deployment does not have readiness or liveness probes configured.

**3. Why is a baseline useful before adding a liveness probe?**

A baseline provides a working reference point. It allows us to compare the Deployment's behavior before and after adding a liveness probe and identify the effect of the health check.


---

# Task 3 — Add a Liveness Probe

## Goal

Add an HTTP liveness probe so Kubernetes can periodically check whether the NGINX container is still responsive.

### Evidence

#### Screenshot 5 — Completed `01-nginx-deploy-liveness.yaml` manifest showing the liveness probe

<img width="1458" height="556" alt="image" src="https://github.com/user-attachments/assets/880fd673-f314-4f50-b44b-8d4223ee93b0" />


---

#### Screenshot 6 — Output showing successful rollout and running Pods

<img width="1354" height="525" alt="image" src="https://github.com/user-attachments/assets/fcfac700-200e-4fa5-b677-c952be323768" />


---

#### Screenshot 7 — Pod description showing liveness-probe details

<img width="1686" height="759" alt="image" src="https://github.com/user-attachments/assets/aa1b2ce8-b7fc-4f53-bdb0-e8a16e05c1b0" />


---

### Notes

**1. What path and port does the liveness probe check?**

It checks the HTTP path / on port 80.

**2. What does `initialDelaySeconds: 10` do?**

It tells Kubernetes to wait 10 seconds after the container starts before performing the first liveness check.

**3. What does `failureThreshold: 3` mean?**

It means Kubernetes allows three consecutive liveness-probe failures before considering the container unhealthy and restarting it.

**4. Does a successful liveness probe control whether a Pod receives traffic? Explain briefly.**

No. A liveness probe does not directly control traffic. It checks whether the container is healthy. A readiness probe determines whether the Pod should receive traffic.


---

# Task 4 — Trigger and Observe a Liveness Restart

## Goal

Intentionally make the liveness probe fail and observe Kubernetes restart the unhealthy container.

### Evidence

#### Screenshot 8 — `02-nginx-liveness-broken.yaml` showing `/does-not-exist`

<img width="717" height="292" alt="image" src="https://github.com/user-attachments/assets/a4ffa19c-4faa-4e5c-aa10-1d6b0709dd71" />


---

#### Screenshot 9 — Pod output showing an increased RESTARTS count

<img width="1207" height="477" alt="image" src="https://github.com/user-attachments/assets/3e322b6b-aa84-4e8a-a455-006c8c93fcf4" />


---

#### Screenshot 10 — Pod description showing liveness-probe failure events or restart details

<img width="1737" height="558" alt="image" src="https://github.com/user-attachments/assets/a0f477d8-1f98-43e9-b891-639a3258e6e5" />


---

#### Screenshot 11 — Output showing stable running Pods after applying the fixed configuration

<img width="1362" height="546" alt="image" src="https://github.com/user-attachments/assets/fc65fdb0-b811-41d3-a492-c488c04e5e9c" />


---

### Notes

**1. Why did the liveness probe fail?**

The liveness probe failed because it was configured to check /does-not-exist, a path that NGINX does not serve successfully. The HTTP request returned an unsuccessful response.

**2. What happened after Kubernetes detected repeated liveness-probe failures?**

After detecting the configured number of consecutive failures, Kubernetes restarted the unhealthy container. The container started again, and Kubernetes continued monitoring it with the liveness probe.

**3. What does the RESTARTS column prove?**

It shows how many times a container has restarted inside its Pod. An increased restart count confirms that Kubernetes restarted the container after detecting liveness-probe failures.


**4. How did you restore the Deployment to a stable state?**

I restored the correct liveness-probe path to / on port 80 and applied the fixed Deployment configuration. The probe then succeeded, and the NGINX containers returned to a stable running state.


---

# Task 5 — Optional: Observe a Restart Loop

## Goal

Observe why overly aggressive or incorrectly configured liveness probes can create restart loops.

Complete this section only if you attempt Task 5. Otherwise, mark it as “Not attempted.”

**Task status:** Completed / Not attempted

### Evidence

#### Optional Screenshot — Pod output showing the RESTARTS count increasing during the restart-loop observation



No specific restart count or CrashLoopBackOff status is required.

---

### Notes — Answer Only If Attempted

**1. What is a restart loop?**

A restart loop occurs when a container repeatedly starts, fails, and gets restarted by Kubernetes because it cannot remain healthy.

**2. Why can an aggressive liveness probe be harmful?**

An overly aggressive probe may restart a container before the application has enough time to initialize or recover. This can cause unnecessary restarts and reduce application availability.

**3. Why should liveness checks be lightweight and carefully tuned?**

Liveness checks should be lightweight to avoid consuming unnecessary resources. They should also have appropriate delays, intervals, and failure thresholds so Kubernetes can detect genuine failures without restarting healthy applications unnecessarily.


---

# Task 6 — Share Your Liveness-Probe Learning on LinkedIn

## Goal

Share what you learned about Kubernetes liveness probes, container restarts, and the difference between readiness and liveness.

### Evidence

#### Screenshot 12 — Published LinkedIn post



#### Linkedin post URL



---

# Submission Instructions

- Add all required screenshots numbered 1–12.
- Include the optional Task 5 screenshot only if you attempt that task.
- Ensure your full name is visible in required screenshots.
- Use clear, readable screenshots showing the relevant manifest or output.
- Include the completed baseline and liveness-probe manifests in your repository.
- Answer all Notes questions for Tasks 1–4 in your own words.
- If you attempt Task 5, complete its Notes and restore the working configuration afterward.
- Do not expose tokens, passwords, kubeconfig files, account IDs, or other sensitive information.

---

# Completion Checklist

- [ ] Learning cluster confirmed and previous assignment resources removed where applicable
- [ ] Liveness-probe lab directory created (Screenshot 1)
- [ ] Baseline Deployment manifest completed (Screenshot 2)
- [ ] Successful rollout and two baseline Pods verified (Screenshot 3)
- [ ] Baseline Deployment details reviewed (Screenshot 4)
- [ ] Liveness probe added successfully (Screenshot 5)
- [ ] Successful liveness-probe rollout verified (Screenshot 6)
- [ ] Liveness-probe details inspected (Screenshot 7)
- [ ] Broken liveness configuration created (Screenshot 8)
- [ ] Increased container restart count observed (Screenshot 9)
- [ ] Liveness-probe failure events or restart details captured (Screenshot 10)
- [ ] Working liveness configuration restored and stable Pods verified (Screenshot 11)
- [ ] Optional Task 5 evidence and Notes completed, if attempted
- [ ] Working configuration restored after Task 5, if attempted
- [ ] LinkedIn post published (Screenshot 12)
- [ ] Notes for Tasks 1–4 completed
- [ ] Required manifests included
- [ ] All required screenshots are clear and readable
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
