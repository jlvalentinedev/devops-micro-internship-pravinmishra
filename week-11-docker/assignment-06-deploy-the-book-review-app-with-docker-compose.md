# Assignment 6 — Deploy the Book Review App with Docker Compose

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will deploy the Book Review Application with Docker Compose using MySQL, a backend API, and a frontend user interface. You will configure health-gated startup, browser-facing API access, CORS, and persistent MySQL storage.

---

# Task 1 — Prepare the Project

## Goal

Prepare your fork of the Book Review App repository for Docker Compose deployment.

### Evidence

#### Screenshot 1 — Project Structure

Add a screenshot showing the project structure containing:

```text
frontend/
backend/
.env.example
.gitignore
docker-compose.yml
```



---

#### Screenshot 2 — Environment and Docker Ignore Files

Add a screenshot showing the contents of:

```text
.env.example
.gitignore
frontend/.dockerignore
backend/.dockerignore
```

Ensure that no real passwords, tokens, or secrets are visible.



---

# Task 2 — Create or Confirm Application Dockerfiles

## Goal

Prepare Dockerfiles for the frontend and backend services and build both services through Docker Compose.

### Evidence

#### Screenshot 3 — Frontend Dockerfile

Add a screenshot showing the completed `frontend/Dockerfile`.

<img width="776" height="482" alt="Ass6-ss3" src="https://github.com/user-attachments/assets/623f4ec4-4f82-4c1c-a0c9-96ede870f0eb" />


---

#### Screenshot 4 — Backend Dockerfile

Add a screenshot showing the completed `backend/Dockerfile`.

<img width="618" height="341" alt="Ass6-ss4" src="https://github.com/user-attachments/assets/538fbfc9-d925-405d-9daa-bc2663ef7ae9" />


---

#### Screenshot 5 — Docker Compose Build

Add a screenshot of the terminal showing successful completion of:

```bash
docker compose build
```

<img width="940" height="482" alt="Ass6-ss5" src="https://github.com/user-attachments/assets/311676f1-9157-484c-a6c1-d2ac0a91d3f8" />


---

# Task 3 — Create the Docker Compose Stack

## Goal

Create one `docker-compose.yml` file that builds and runs MySQL, backend, and frontend services.

### Evidence

#### Screenshot 6 — MySQL Service, Health Check, and Volume Mount

Add a screenshot showing the MySQL service in `docker-compose.yml`, including:

- MySQL image
- Environment variables
- MySQL health check
- `mysql_data` volume mount
- No published MySQL port



---

#### Screenshot 7 — Backend Configuration

Add a screenshot showing the backend service configuration, including:

- `depends_on` with `condition: service_healthy`
- Database host set to `mysql`
- Browser frontend origin configured for CORS
- Published backend port

<img width="609" height="375" alt="Ass6-ss7" src="https://github.com/user-attachments/assets/08f63d4a-1fa9-4cea-8d15-e98ef00c08ea" />


---

#### Screenshot 8 — Frontend Configuration

Add a screenshot showing the frontend service configuration, including:

- Published frontend port
- `depends_on` for the backend service
- Browser-facing `NEXT_PUBLIC_API_URL`

<img width="662" height="561" alt="Ass6-ss8" src="https://github.com/user-attachments/assets/bacd0477-5cfb-4374-b7e1-f0aec29901d2" />


---

#### Screenshot 9 — Named Volume Definition

Add a screenshot showing the `mysql_data` volume definition in `docker-compose.yml`.

<img width="1042" height="412" alt="Ass6-ss9" src="https://github.com/user-attachments/assets/86768327-2171-477b-b733-127d0b19e9c2" />


---

# Task 4 — Start and Verify the Stack

## Goal

Build and start all services through one Docker Compose workflow.

### Evidence

#### Screenshot 10 — Docker Compose Service Status

Add a screenshot of the terminal showing:

```bash
docker compose ps
```

The output must show the MySQL, backend, and frontend services running. MySQL must show as healthy.

<img width="1271" height="223" alt="Ass6-ss10" src="https://github.com/user-attachments/assets/65c38769-1b46-4ed0-9d5d-b51c535f022c" />


---

#### Screenshot 11 — MySQL and Backend Logs

Add a screenshot of the terminal showing:

```bash
docker compose logs mysql backend --tail=50
```

The logs must show MySQL readiness and successful backend database connection.

<img width="1035" height="483" alt="Ass6-ss11" src="https://github.com/user-attachments/assets/41e19979-82f7-43ec-9901-b9bccba76f62" />


---

# Task 5 — Test End-to-End Application Functionality

## Goal

Verify that the Book Review App works through the browser.

### Evidence

#### Screenshot 12 — Successful Registration or Login

Add a browser screenshot showing successful user registration or login.

Add your full name as a clear caption directly below the screenshot.

<img width="987" height="416" alt="Ass6-ss12" src="https://github.com/user-attachments/assets/5df72b50-9805-4209-968c-8b17ad277ae9" />


---

#### Screenshot 13 — Created Book Review

Add a browser screenshot showing a created book review visible in the application.

Add your full name as a clear caption directly below the screenshot.

<img width="1365" height="421" alt="Ass6-ss13" src="https://github.com/user-attachments/assets/9e49f276-894f-4394-9e80-8ad303ebc01d" />


---

#### Screenshot 14 — CORS Verification

Add a browser developer-tools screenshot with:

- The Network tab showing a successful API request
- The Console drawer showing no CORS error after the API interaction



---

# Task 6 — Prove MySQL Data Persistence

## Goal

Verify that MySQL data remains after a non-destructive Docker Compose down/up cycle.

### Evidence

#### Screenshot 15 — Data Before Restart

Add a browser screenshot showing the registered user or created review before the down/up cycle.

Add your full name as a clear caption directly below the screenshot.

<img width="859" height="360" alt="Ass6-ss15" src="https://github.com/user-attachments/assets/8cd30e49-1a9e-4f42-9752-469a82d7da13" />


---

#### Screenshot 16 — Non-Destructive Stack Restart

Add a screenshot of the terminal showing the non-destructive shutdown and restart:

```bash
docker compose down
docker compose up -d
docker compose ps
```

Do not use `docker compose down -v`.

<img width="1331" height="307" alt="Ass6-ss16" src="https://github.com/user-attachments/assets/24524a42-90fe-4b43-9305-10a0b4658e88" />


---

#### Screenshot 17 — Data After Restart

Add a browser screenshot showing the same registered user or review after the stack restarts.

Add your full name as a clear caption directly below the screenshot.



---

# Task 7 — Explain Docker Compose Teardown Modes

## Goal

Explain the difference between preserving data and fully resetting a Docker Compose environment.

### Notes

Write a short explanation of 5–8 lines covering:

- What `docker compose down` removes and preserves
- Why named volumes should be kept when preserving MySQL data
- What happens when named volumes are removed
- When a full reset is useful
- Why a full reset must not be used before persistence evidence is captured

The `docker compose down` command stops and removes the Compose containers and default networks but preserves named volumes by default.  
Named volumes should be kept when preserving MySQL data because they store database files independently of the containers.  
When named volumes are removed using `docker compose down -v`, the stored MySQL data is permanently deleted.  
A full reset is useful when starting a fresh environment, troubleshooting configuration issues, or removing all previous application data.  
The full reset should only be performed when intentionally discarding the existing data.  
It must not be used before capturing persistence evidence because removing the volumes would destroy the data needed to demonstrate that persistence works.  
Therefore, always capture the required screenshots and verify important data before performing a full reset.

---

# Final Public Frontend URL

**Frontend URL:** `

Replace the placeholder with your working application URL.

---

# GitHub Repository URL

**Your Fork or Repository URL:** `

---

# LinkedIn Requirement

## Goal

Create a LinkedIn post about the Book Review App deployment and what you learned from using Docker Compose.

### Evidence

**LinkedIn Post URL:** ``

#### LinkedIn Post Screenshot

Add a screenshot of your published LinkedIn post here.

---

# Submission Checklist

- [ ] Book Review App repository forked and used
- [ ] `.env` excluded from Git tracking
- [ ] `.env.example` contains only safe placeholder values
- [ ] Frontend and backend Dockerfiles created or confirmed
- [ ] MySQL health check configured
- [ ] Backend waits for healthy MySQL
- [ ] Backend uses `mysql` as the database hostname
- [ ] Frontend API URL uses the VM public IP and backend port
- [ ] Backend CORS origin matches the frontend origin
- [ ] MySQL port 3306 is not publicly exposed
- [ ] Registration and login work
- [ ] Book review creation works
- [ ] Data persists after a non-destructive down/up cycle
- [ ] Screenshots 1–17 included
- [ ] Teardown explanation completed
- [ ] Public frontend URL included
- [ ] GitHub repository URL included
- [ ] LinkedIn post URL and screenshot included
- [ ] Full name visible in required terminal screenshots
- [ ] Browser screenshots include a full-name caption
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
