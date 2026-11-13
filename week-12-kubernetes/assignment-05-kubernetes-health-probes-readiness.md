# Assignment 5 — Kubernetes Health Probes (Readiness)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will configure and test a Kubernetes readiness probe. You will create a baseline NGINX Deployment, add an HTTP readiness probe, intentionally break it, observe a stalled rollout, and restore the working configuration.

You will also demonstrate how readiness probes protect rolling updates.

---

# Task 0 — Prepare the Lab Environment

## Goal

Confirm that you are connected to your learning cluster and remove the previous assignment’s HPA and NGINX Deployment before starting this lab.

No screenshot or written notes are required for this pre-check.

---

# Task 1 — Set Up Your Lab Directory

## Goal

Create and enter a dedicated directory for the readiness-probe lab.

### Evidence

#### Screenshot 1 — Terminal showing that you are working inside `~/k8s-labs/health-probes-readiness`

<img width="820" height="274" alt="image" src="https://github.com/user-attachments/assets/41c8d82d-0bea-4497-b083-39b8df252983" />


---

### Notes

**1. What is the purpose of a readiness probe?**

A readiness probe checks whether a container is ready to accept traffic. Kubernetes uses the result to determine whether the Pod should receive traffic through its Service.

**2. Why is a Pod being Running not always enough to confirm it can serve traffic?**

Running only means the container has started. The application inside it may still be initializing, loading dependencies, or experiencing errors. A readiness probe confirms whether it is actually ready to handle requests.

---

# Task 2 — Create a Baseline Deployment Without Probes

## Goal

Create a baseline NGINX Deployment with two replicas and no readiness probe.

### Evidence

#### Screenshot 2 — Completed `00-nginx-deploy-baseline.yaml` manifest

<img width="1125" height="612" alt="image" src="https://github.com/user-attachments/assets/bcaaec3c-d297-4e31-9fa3-15eb95b416be" />


---

#### Screenshot 3 — Output showing a successful rollout and two running NGINX Pods

<img width="1302" height="247" alt="image" src="https://github.com/user-attachments/assets/3c778951-4f62-4acf-8bbf-ae073930685c" />


---

#### Screenshot 4 — Relevant output from `kubectl describe deployment nginx-deployment`

<img width="1743" height="433" alt="image" src="https://github.com/user-attachments/assets/52d1b5be-f669-442e-9f0e-6cd5a91ea8c8" />


---

### Notes

**1. How many replicas does this Deployment maintain?**

The Deployment maintains two replicas of the NGINX Pod.

**2. What does `maxUnavailable: 0` mean during a rolling update?**

It means Kubernetes must not allow the number of available Pods to fall below the desired replica count during a rolling update. Existing healthy Pods remain available while replacements are created.

**3. Is a readiness probe configured in this baseline Deployment?**

No. The baseline Deployment does not have a readiness probe configured.


---

# Task 3 — Add a Readiness Probe

## Goal

Add an HTTP readiness probe so Kubernetes checks whether each NGINX container is ready to accept requests.

### Evidence

#### Screenshot 5 — Completed `01-nginx-deploy-readiness.yaml` manifest showing the readiness probe

<img width="1107" height="748" alt="image" src="https://github.com/user-attachments/assets/89c9101a-bf6d-4dfe-a7af-53f6e2fcf78e" />


---

#### Screenshot 6 — Output of the successful rollout and ready Pods

<img width="1351" height="160" alt="image" src="https://github.com/user-attachments/assets/9a946c78-b9cc-4d7d-bf08-e72d2b17277c" />


---

#### Screenshot 7 — Pod description showing readiness conditions and readiness probe details

<img width="1225" height="235" alt="image" src="https://github.com/user-attachments/assets/28a32077-253b-4450-8ac9-9d80890e54dd" />


---

### Notes

**1. What path and port does the readiness probe check?**

It checks the HTTP path / on port 80.

**2. What does `initialDelaySeconds: 2` do?**

It tells Kubernetes to wait two seconds after the container starts before performing the first readiness probe.

**3. What does `periodSeconds: 5` do?**

It tells Kubernetes to perform the readiness check every five seconds.

**4. What must happen before Kubernetes considers this Pod ready?**

The NGINX container must respond successfully to the HTTP readiness check on the configured path and port. Kubernetes then marks the Pod as Ready.

---

# Task 4 — Break and Restore Readiness

## Goal

Intentionally fail the readiness probe, observe the NotReady behavior, and then restore the working probe configuration.

### Evidence

#### Screenshot 8 — `02-nginx-readiness-broken.yaml` showing `/does-not-exist`

<img width="1392" height="223" alt="image" src="https://github.com/user-attachments/assets/b81f17e2-4165-48a4-974d-9e39231c0d92" />


---

#### Screenshot 9 — Output showing the rollout timeout or incomplete rollout

<img width="1449" height="154" alt="image" src="https://github.com/user-attachments/assets/8101986d-c2aa-4ffe-800a-0df21c53f3ff" />


---

#### Screenshot 10 — Pod details showing `Ready: False` or readiness-probe failure events

<img width="1527" height="787" alt="image" src="https://github.com/user-attachments/assets/ec665359-7502-4faa-ad8d-6b0265cd1fa9" />


---

#### Screenshot 11 — Output showing successful rollout and ready Pods after the fix

<img width="1315" height="181" alt="image" src="https://github.com/user-attachments/assets/e59469ce-2469-4a11-9d71-1d771c7d2124" />


---

### Notes

**1. Why did the readiness probe fail?**

The readiness probe failed because it was configured to check /does-not-exist, a path that NGINX does not serve successfully. The HTTP request returned an unsuccessful response.

**2. What happened to the Pod readiness status?**

The Pod remained Running, but its readiness status changed to False. Kubernetes therefore treated it as not ready to receive traffic.

**3. Why did the rollout fail to complete?**

The rollout could not complete because the new Pod failed its readiness checks. Kubernetes waited for a ready replacement before proceeding with the rolling update.

**4. How did you restore the Deployment successfully?**

I restored the correct readiness probe path to / on port 80 and applied the corrected Deployment configuration. The readiness checks then succeeded, and the rollout completed successfully.

---

# Task 5 — See How Readiness Protects Rolling Updates

## Goal

Observe how readiness prevents a bad new Pod from replacing healthy Pods during a rolling update.

### Evidence

#### Screenshot 12 — Successful update command and rollout status

<img width="1494" height="282" alt="image" src="https://github.com/user-attachments/assets/ec6fb0d8-6dde-46b4-a497-9c7fb8261734" />


---

#### Screenshot 13 — ReplicaSets and Pods after the successful rolling update

<img width="1812" height="403" alt="image" src="https://github.com/user-attachments/assets/e4d78ca3-0eea-4179-912c-cfdd45ba2d5d" />


---

#### Screenshot 14 — Completed `04-readiness-broken-patch.yaml`

<img width="1159" height="495" alt="image" src="https://github.com/user-attachments/assets/925c3afe-ec57-4790-b15a-bd5476e426b7" />


---

#### Screenshot 15 — Output showing the expected stalled rollout or timeout

<img width="1474" height="177" alt="image" src="https://github.com/user-attachments/assets/487cf975-58f4-4561-9441-9eb644dfda0c" />


---

#### Screenshot 16 — Deployment or Pod output showing the effect of the broken readiness probe

<img width="1282" height="376" alt="image" src="https://github.com/user-attachments/assets/a57f3baa-731d-4b88-ad42-b159dab63457" />


---

#### Screenshot 17 — Successful rollout status after restoring the fixed configuration

<img width="1383" height="454" alt="image" src="https://github.com/user-attachments/assets/727cab46-8180-42de-948b-a1591f45451e" />


---

### Notes

**1. What happened during the successful rolling update?**

Kubernetes gradually created new Pods, waited for them to become Ready, and then replaced the old Pods. The application remained available throughout the update.

**2. Why did Kubernetes create a new ReplicaSet?**

A change to the Deployment's Pod template triggered Kubernetes to create a new ReplicaSet. The new ReplicaSet manages Pods using the updated configuration.

**3. Why were the new Pods unable to replace the existing healthy Pods after readiness was broken?**

The new Pods failed their readiness probes and were not considered available. Kubernetes therefore kept the existing healthy Pods running instead of replacing them with unready Pods.

**4. How does `maxUnavailable: 0` protect availability during this rollout?**

It prevents Kubernetes from reducing the number of available Pods below the desired replica count during the rolling update. This helps ensure that healthy Pods remain available while new Pods are being tested.

---

# Task 6 — Share Your Readiness-Probe Learning on LinkedIn

## Goal

Share what you learned about Kubernetes readiness probes and how they protect rolling updates.

### Evidence

#### Screenshot 18 — Published LinkedIn post



#### Linkedin post link



---

# Submission Instructions

- Add all required screenshots numbered 1–18.
- Ensure your full name is visible in required screenshots.
- Use clear, readable screenshots showing the relevant manifest or output.
- Include the completed baseline and readiness-probe manifests in your repository.
- Answer all Notes questions for Tasks 1–5 in your own words.
- Include evidence of the intentional readiness failure and successful recovery.
- Do not expose tokens, passwords, kubeconfig files, account IDs, or other sensitive information.

---

# Completion Checklist

- [ ] Learning cluster confirmed and previous assignment resources removed where applicable
- [ ] Readiness-probe lab directory created (Screenshot 1)
- [ ] Baseline Deployment created successfully (Screenshot 2)
- [ ] Two baseline Pods running and successful rollout verified (Screenshot 3)
- [ ] Baseline Deployment details reviewed (Screenshot 4)
- [ ] Readiness probe added successfully (Screenshot 5)
- [ ] Successful readiness rollout verified (Screenshot 6)
- [ ] Pod readiness conditions and probe details inspected (Screenshot 7)
- [ ] Broken readiness configuration created (Screenshot 8)
- [ ] Stalled rollout or timeout observed (Screenshot 9)
- [ ] NotReady status or readiness-probe failure events captured (Screenshot 10)
- [ ] Working readiness configuration restored (Screenshot 11)
- [ ] Successful image update completed (Screenshot 12)
- [ ] ReplicaSets and Pods inspected after the update (Screenshot 13)
- [ ] Broken-readiness patch created (Screenshot 14)
- [ ] Stalled rollout observed after the patch (Screenshot 15)
- [ ] Effect of broken readiness captured (Screenshot 16)
- [ ] Final recovery completed (Screenshot 17)
- [ ] LinkedIn post published (Screenshot 18)
- [ ] Notes for Tasks 1–5 completed
- [ ] Required manifests included
- [ ] All screenshots are clear and readable
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
