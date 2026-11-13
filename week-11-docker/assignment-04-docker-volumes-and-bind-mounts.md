# Assignment 4 — Docker Volumes and Bind Mounts

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will use Docker Bind Mounts and Docker Volumes to persist logs and application data outside a container’s lifecycle. You will verify that data remains available after containers are removed and recreated.

---

# Task 1 — Persist Nginx Logs Using a Bind Mount

## Goal

Deploy an Nginx container with a Bind Mount and verify that its log files remain on the VM host after the container is removed.

### Evidence

#### Screenshot 1 — Nginx Image Pull

Add a screenshot of the terminal showing successful completion of:

```bash
docker pull nginx:alpine
```

<img width="784" height="100" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/6f03e43c-09e5-4a71-a824-a3f3e86b55b2" />


---

#### Screenshot 2 — Host Log Directory

Add a screenshot of the terminal showing the created host directory:

```text
$HOME/nginx-logs
```

<img width="784" height="100" alt="Ass4-ss2" src="https://github.com/user-attachments/assets/47237afd-a813-4a4b-9fbf-441be9d5dc92" />


---

#### Screenshot 3 — Running Nginx Container with Port Mapping

Add a screenshot of the terminal showing:

```bash
docker ps
```

The output must show the `myweb` container with:

```text
0.0.0.0:80->80/tcp
```

<img width="1036" height="172" alt="Ass4-ss3" src="https://github.com/user-attachments/assets/b1e927cd-063e-420a-ab82-bff7241b5371" />


---

#### Screenshot 4 — Nginx Welcome Page

Add a browser screenshot showing the Nginx Welcome Page at:

```text
http://<YOUR-VM-PUBLIC-IP>
```

Ensure that the VM public IP is visible in the address bar. Add your full name as a clear caption directly below the screenshot.

<img width="845" height="497" alt="Ass4-ss4" src="https://github.com/user-attachments/assets/ba8f484f-ea28-435d-88e4-10772b5e1e93" />


---

#### Screenshot 5 — Bind-Mounted Log Files

Add a screenshot of the terminal showing the host log files and access-log content from:

```text
$HOME/nginx-logs
```

The output must show `access.log`, `error.log`, and an access-log entry created when you opened the Nginx page.

<img width="734" height="115" alt="Ass4-ss5" src="https://github.com/user-attachments/assets/b8e67468-5023-48bb-92ad-2b3b8b4d088d" />


---

#### Screenshot 6 — Nginx Container Removed

Add a screenshot of the terminal showing successful completion of:

```bash
docker stop myweb
docker rm myweb
```

<img width="525" height="162" alt="Ass4-ss6" src="https://github.com/user-attachments/assets/3dc5d86a-f2cc-471c-8513-49928909b2c3" />


---

#### Screenshot 7 — Logs Persist After Container Removal

Add a screenshot of the terminal showing that `access.log` and `error.log` still exist in:

```text
$HOME/nginx-logs
```

The access log must retain its content after the container has been removed.

<img width="720" height="117" alt="Ass4-ss7" src="https://github.com/user-attachments/assets/89b5e2a5-c4ab-4558-9764-72dc9c2b931b" />


---

# Task 2 — Share Persistent Data Using a Docker Volume

## Goal

Deploy backend and frontend containers that share data through a named Docker Volume. Verify that the data remains after both containers are removed and recreated.

### Evidence

#### Screenshot 8 — Project File Structure

Add a screenshot of the terminal showing the `two-tier-app` project structure, including separate `backend` and `frontend` directories with a `Dockerfile` and `index.js` file in each.

<img width="618" height="242" alt="Ass4-ss8" src="https://github.com/user-attachments/assets/525978d9-6893-4316-ba71-2056597255a3" />


---

#### Screenshot 9 — Custom Docker Network

Add a screenshot of the terminal showing `mynetwork` in:

```bash
docker network ls
```

<img width="693" height="218" alt="Ass4-ss9" src="https://github.com/user-attachments/assets/78efdbbb-83d5-4fbd-8381-7d49c16da8a0" />


---

#### Screenshot 10 — Docker Volume

Add a screenshot of the terminal showing `shared-data` in:

```bash
docker volume ls
```

<img width="747" height="196" alt="Ass4-ss10" src="https://github.com/user-attachments/assets/e22460bb-7e34-43b9-9a5f-7a4030e19520" />


---

#### Screenshot 11 — Backend Dockerfile

Add a screenshot of the terminal showing the completed backend `Dockerfile`.

<img width="780" height="444" alt="Ass4-ss11" src="https://github.com/user-attachments/assets/39866a07-765d-4782-ac1e-c32a3369c492" />


---

#### Screenshot 12 — Backend Image Build

Add a screenshot of the terminal showing successful completion of the `backend-app:latest` image build.

<img width="701" height="293" alt="Ass4-ss12" src="https://github.com/user-attachments/assets/c6115236-b9fd-4ef9-b49b-bc3f4afec1df" />


---

#### Screenshot 13 — Running Backend Container

Add a screenshot of the terminal showing:

```bash
docker ps
```

The output must show the running `backend` container.

<img width="1020" height="156" alt="Ass4-ss13" src="https://github.com/user-attachments/assets/df2cc5f0-3efb-4af5-b513-23f359ca91dd" />


---

#### Screenshot 14 — Frontend Dockerfile

Add a screenshot of the terminal showing the completed frontend `Dockerfile`.

<img width="735" height="439" alt="Ass4-ss14" src="https://github.com/user-attachments/assets/9f576a74-325c-49d8-9613-6c7ef171c569" />


---

#### Screenshot 15 — Frontend Image Build

Add a screenshot of the terminal showing successful completion of the `frontend-app:latest` image build.

<img width="793" height="200" alt="Ass4-ss15" src="https://github.com/user-attachments/assets/4b614019-007f-4bc6-8c2b-ef03ead14f50" />


---

#### Screenshot 16 — Running Backend and Frontend Containers

Add a screenshot of the terminal showing:

```bash
docker ps
```

The output must show both `backend` and `frontend` containers running. Only `frontend` must have the published port mapping:

```text
0.0.0.0:80->80/tcp
```

<img width="1024" height="222" alt="Ass4-ss16" src="https://github.com/user-attachments/assets/7904776f-1574-415a-a1e6-74ec84dfb083" />


---

#### Screenshot 17 — Backend Write Operation

Add a screenshot of the terminal showing a successful backend write operation to the shared Docker Volume.

The output must include:

```text
Data written: Hello from Backend!
```

<img width="1018" height="262" alt="Ass4-ss17" src="https://github.com/user-attachments/assets/7d8368d3-8f3a-4c40-b306-1d18925fbe68" />


---

#### Screenshot 18 — Frontend Reads Shared Data

Add a browser screenshot showing:

```text
Hello from Backend!
```

Add your full name as a clear caption directly below the screenshot.

<img width="868" height="266" alt="Ass4-ss18" src="https://github.com/user-attachments/assets/316ce08f-8946-4fc5-ab85-4fbde42d47af" />


---

#### Screenshot 19 — First Shared-Data Update

Add a browser screenshot showing:

```text
Test Data 1
```

Add your full name as a clear caption directly below the screenshot.

<img width="975" height="370" alt="Ass4-ss19" src="https://github.com/user-attachments/assets/37947b35-8490-4070-bf5e-37444343dcd8" />


---

#### Screenshot 20 — Second Shared-Data Update

Add a browser screenshot showing:

```text
Test Data 2 - New Update
```

Add your full name as a clear caption directly below the screenshot.

<img width="926" height="360" alt="Ass4-ss20" src="https://github.com/user-attachments/assets/d2b05e01-61dc-40f1-8485-5bcc93b77afe" />


---

#### Screenshot 21 — Container Removal and Recreation

Add a screenshot of the terminal showing the `frontend` and `backend` containers removed and recreated using the same `shared-data` Docker Volume.



---

#### Screenshot 22 — Data Persists After Recreation

Add a browser screenshot showing:

```text
Test Data 2 - New Update
```

This proves that the `shared-data` Docker Volume outlived both application containers.

Add your full name as a clear caption directly below the screenshot.

<img width="877" height="445" alt="Ass4-ss22" src="https://github.com/user-attachments/assets/7d9530d2-0fb9-43f4-99a4-f584425969f6" />


---

# Storage Persistence Notes

Write a short explanation covering:

- The difference between a Bind Mount and a Docker Volume
- How Task 1 proved Bind Mount persistence
- How Task 2 proved Docker Volume persistence
- Why Docker Volumes are commonly used for application data

1. **Bind Mount vs Docker Volume:** A Bind Mount connects a specific directory or file on the host machine to a container, while a Docker Volume is managed by Docker and stored in its dedicated storage area.

2. **Task 1 — Bind Mount Persistence:** Task 1 demonstrated Bind Mount persistence by storing data in a host directory, deleting or recreating the container, and confirming that the data remained available.

3. **Task 2 — Docker Volume Persistence:** Task 2 demonstrated Docker Volume persistence by storing data in a Docker-managed volume and confirming that the data remained intact even after the container was removed and recreated.

4. **Why Docker Volumes Are Commonly Used:** Docker Volumes are commonly used for application data because they persist independently of containers, are managed by Docker, support easier backups and migration, and provide reliable storage for databases and other stateful applications.

---

# Public Application URL

**Application URL:** 

---

# LinkedIn Requirement

## Goal

Create a LinkedIn post about Docker Volumes and Bind Mounts, including one difference between them, how you verified persistent storage, and your key learning outcomes.

### Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:



---

#### LinkedIn Post Screenshot

Add a screenshot of the published LinkedIn post here. Include a screenshot of the application displaying shared data.

---

# Submission Instructions

- Complete all tasks in sequence.
- Include Screenshots 1–22 exactly as specified.
- Include the Storage Persistence Notes section.
- Include the public application URL.
- Include the LinkedIn post URL and screenshot.
- Ensure that your full name is visible in all terminal screenshots.
- Add your full name as a clear caption below every browser screenshot.
- Do not expose private keys, passwords, access keys, tokens, account IDs, or other sensitive information.

---

# Completion Checklist

- [ ] Nginx image pulled successfully
- [ ] Host log directory created
- [ ] Bind Mount configured successfully
- [ ] Nginx logs remain after container removal
- [ ] Custom Docker network created
- [ ] Docker Volume created
- [ ] Backend Dockerfile and image created
- [ ] Frontend Dockerfile and image created
- [ ] Both containers mount `shared-data`
- [ ] Backend writes data to the Docker Volume
- [ ] Frontend reads the same data from the Docker Volume
- [ ] Updated data appears after browser refresh
- [ ] Data remains after frontend and backend containers are removed and recreated
- [ ] All required screenshots included
- [ ] Storage Persistence Notes completed
- [ ] Public application URL included
- [ ] LinkedIn post URL and screenshot included
- [ ] Full name visible in terminal screenshots
- [ ] Browser screenshots have full-name captions
- [ ] No sensitive information exposed

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
