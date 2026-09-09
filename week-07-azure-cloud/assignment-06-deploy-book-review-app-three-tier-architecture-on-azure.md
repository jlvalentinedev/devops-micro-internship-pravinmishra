# Assignment 6 — Capstone: Deploy Book Review App (Three-Tier Architecture) on Azure

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

This is the most important assignment of the course. You will deploy the Book Review App in a production-ready, best-practice-compliant three-tier architecture on Azure: separated presentation, application, and database tiers, least-privilege network access, a controlled public entry point, protected secrets, and availability/monitoring evidence.

---

# Task 1 — Design the Azure Three-Tier Architecture

## Goal

Create an architecture diagram and implementation plan identifying the presentation, application, and database components, the chosen Azure services, the public entry point, and the internal traffic paths.

### Evidence

#### Screenshot 1 — Architecture diagram showing the public entry point, three tiers, network boundaries, and traffic flow

![azure](screenshots/azurediagram.png)

---

#### Screenshot 2 — Written architecture assumptions and selected Azure services

# Book Review App — Architecture Assumptions and Selected Azure Services

## Architecture Assumptions

The Book Review App will be deployed using a three-tier architecture that separates the presentation, application, and database layers. The design is intended to improve security, scalability, availability, and maintainability.

* The Azure deployment will use a dedicated **Virtual Network (VNet)** with separate subnets for each application tier.
* The **Web/Presentation Tier** will host the Next.js frontend and Nginx reverse proxy.
* The **Application Tier** will host the Node.js/Express backend API and will not be directly accessible from the public Internet.
* The **Database Tier** will use a private MySQL database that can only receive connections from the application tier.
* A public **Application Gateway** will serve as the controlled entry point for users accessing the application.
* Network Security Groups (NSGs) will restrict traffic between tiers using the principle of least privilege.
* Application and database servers will use private IP addresses where public access is not required.
* Application secrets and database credentials will be stored securely rather than being hard-coded in the application.
* The architecture will support availability across multiple Azure availability zones where the selected Azure services and region support them.
* Monitoring, logging, backups, and health checks will be enabled to help maintain the application in a production environment.

## Selected Azure Services

| Architecture Component | Azure Service                                  | Purpose                                                                              |
| ---------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------ |
| Public Entry Point     | **Azure Application Gateway**                  | Receives external web traffic and routes requests to the web tier.                   |
| Network                | **Azure Virtual Network (VNet)**               | Provides the private network environment for the application.                        |
| Web Tier               | **Azure Virtual Machines / VM Scale Set**      | Hosts Nginx and the Next.js frontend.                                                |
| Application Tier       | **Azure Virtual Machines / VM Scale Set**      | Hosts the Node.js/Express backend API.                                               |
| Database Tier          | **Azure Database for MySQL – Flexible Server** | Provides managed MySQL database services with private network connectivity.          |
| Network Security       | **Network Security Groups (NSGs)**             | Controls and restricts traffic between the different tiers.                          |
| Secrets                | **Azure Key Vault**                            | Stores database credentials, application secrets, and other sensitive configuration. |
| Monitoring             | **Azure Monitor / Application Insights**       | Collects application and infrastructure logs, metrics, and alerts.                   |
| Storage/Backup         | **Azure-managed backups**                      | Provides database backup and recovery capabilities.                                  |

## Traffic Flow

**Internet User → Application Gateway → Web Tier → Application Tier → MySQL Database**

Only the Application Gateway is exposed as the public entry point. The application and database tiers remain protected behind private network boundaries, with NSGs controlling which traffic is allowed between the tiers.


---

# Task 2 — Create the Azure Network Foundation

## Goal

Create a dedicated Resource Group and VNet with separate subnets for the web, application, and database tiers, keeping the application and database tiers without direct public access.

### Evidence

#### Screenshot 3 — Resource Group overview showing the assignment resources

![azure](screenshots/az-assign6screen3.png)

---

#### Screenshot 4 — VNet overview showing the address space and all required subnets

![azure](screenshots/az-assign6screen4.png)

---

#### Screenshot 5 — Route-table or Private DNS evidence where applicable

![azure](screenshots/az-assign6screen5.png)

---

# Task 3 — Configure Security and Secret Management

## Goal

Apply least-privilege NSG rules so traffic flows Internet → public entry point → web tier → application tier → database tier, and store credentials in Azure Key Vault or another approved secure mechanism.

### Evidence

#### Screenshot 6 — NSG rules proving least-privilege access between the tiers

![azure](screenshots/az-assign6screen6.png)

---

#### Screenshot 7 — Key Vault or approved secret-management configuration (without displaying secret values)

N/A

---

# Task 4 — Deploy the Presentation (Web) Tier

## Goal

Deploy the Book Review App presentation layer on the approved web-tier compute service, configured to route requests to the internal application-tier endpoint, and not directly exposed except through the public entry service.

### Evidence

#### Screenshot 8 — Web-tier compute overview showing subnet and availability configuration

![azure](screenshots/az-task4screen8.png)

---
![azure](screenshots/az-task4screen8-1.png)


#### Screenshot 9 — Terminal or service output proving the presentation layer is running


![azure](screenshots/az-task4screen9.png)
---



# Task 5 — Deploy the Business (Application) Tier

## Goal

Deploy the Book Review App backend privately in the application subnet, configured to use the private database endpoint and secured environment values, reachable only through its internal endpoint.

### Evidence

#### Screenshot 10 — Application-tier compute overview showing private subnet placement

![azure](screenshots/az-task4screen10.png)

---

#### Screenshot 11 — Backend process, service, or listening-port evidence

![azure](screenshots/az-task4screen11.png)

---

#### Screenshot 12 — Internal health-check or API response (without exposing secrets)

![azure](screenshots/aztask5screen12.png)

---

# Task 6 — Deploy the Managed Database Tier

## Goal

Create a private Azure managed database (public access disabled), with availability/backup/retention settings, the Book Review App schema imported, and access restricted to the application tier only.

### Evidence

#### Screenshot 13 — Database overview showing private connectivity and public access disabled

![azure](screenshots/aztask5screen13.png)

---

#### Screenshot 14 — Availability, backup, and retention configuration

![azure](screenshots/aztask6screen14.png)

---

#### Screenshot 15 — Successful schema or connectivity verification (without exposing credentials)


![azure](screenshots/aztask6-screen15.png)
---

# Task 7 — Configure Traffic Management, Availability, and Monitoring

## Goal

Configure the approved public entry service with health probes and backend pools, internal routing for the application tier where required, and enable Azure Monitor/diagnostics/logs/alerts for the key resources.

### Evidence

#### Screenshot 16 — Public entry service showing listener, frontend endpoint, and healthy web targets

![azure](screenshots/aztask7screen16-1.png)

---

#### Screenshot 17 — Internal application-tier load-balancing or routing configuration where applicable

![azure](screenshots/aztask7screen16.png)

---

#### Screenshot 18 — Azure Monitor, diagnostic settings, logs, metrics, or alert evidence

![azure](screenshots/aztask7screen18.png)
---

# Task 8 — Validate the Production-Style Deployment

## Goal

Confirm the Book Review App works end to end through the public endpoint, with at least one database read and one write, confirm private tiers are not internet-reachable, and complete a safe availability test.

### Evidence

#### Screenshot 19 — Browser showing the Book Review App through the public endpoint

![azure](screenshots/aztask7screen19.png)

---

#### Screenshot 20 — Proof of successful database-backed read and write operations

![azure](screenshots/aztask8screen20.png)

---

#### Screenshot 21 — Evidence that private tiers are not publicly accessible

![azure](screenshots/aztask8screen21.png)

---

#### Screenshot 22 — Availability-test and healthy-target evidence

![azure](screenshots/aztask8screen22.png)

---

#### Public Endpoint

http://20.220.98.85


---

### Notes

Summarize what worked, issues encountered and how they were fixed, and the availability/security/secrets/monitoring/backup choices made.

Write your answer here.

---

# Submission Instructions

- Add all required screenshots and links in your submission
- Do not expose passwords, keys, connection strings, or subscription IDs

---

# Completion Checklist

- [✅] Task 1: Architecture diagram and assumptions documented (Screenshots 1–2)
- [✅] Task 2: Network foundation created with isolated tiers (Screenshots 3–5)
- [✅] Task 3: Least-privilege security and secret management configured (Screenshots 6–7)
- [✅] Task 4: Presentation tier deployed (Screenshots 8–9)
- [✅] Task 5: Application tier deployed privately (Screenshots 10–12)
- [✅] Task 6: Managed database tier deployed privately (Screenshots 13–15)
- [✅] Task 7: Public entry, internal routing, and monitoring configured (Screenshots 16–18)
- [✅] Task 8: End-to-end validation and availability test completed (Screenshots 19–22, Public Endpoint, Notes)
- [✅] No sensitive data exposed

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
