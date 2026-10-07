# Capstone Assignment — Deploy the Book Review App Using Terraform and Claude Code Agentic AI

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Student Details

**Full Name:** Add your full name here  
**Cloud Platform:** AWS or Azure  
**GitHub Repository URL:** Add your repository URL here  
**Public Application URL / Load-Balancer DNS:** Add the public URL or DNS here

---

## Purpose

Deploy the Book Review App using Terraform on AWS or Azure in a secure, highly available, production-style three-tier architecture. Use Claude Code, specialized subagents, Terraform MCP, and validation hooks to support the engineering workflow while keeping all infrastructure-changing operations under human control.

---

# Task 0 — Prepare the Project and Agentic AI Environment

## Goal

Prepare the Book Review App project and configure the provided Claude Code Agentic AI starter kit with project context, specialized subagents, Terraform MCP, validation hooks, and safety guardrails.

## Evidence

### Screenshot 1 — Project `CLAUDE.md`

Add a screenshot of the project `CLAUDE.md` showing the three-tier architecture, security boundaries, Terraform requirements, and human-approval rules.

<img width="988" height="596" alt="Ass5-ss1a" src="https://github.com/user-attachments/assets/75bcaebb-e991-47db-926b-fbd064693972" />
<img width="1011" height="419" alt="Ass5-ss1b" src="https://github.com/user-attachments/assets/16153b17-5f23-405d-a309-1a3f174310b0" />


---

### Screenshot 2 — Terraform Engineer Subagent

Add a screenshot showing the Terraform Engineer subagent configuration.

<img width="1337" height="620" alt="Ass5-ss2" src="https://github.com/user-attachments/assets/0432323d-b95f-4c1a-9e02-36a5b1d20e4c" />


---

### Screenshot 3 — Architecture and Security Reviewer Subagent

Add a screenshot showing the Architecture and Security Reviewer subagent configuration.

<img width="1315" height="745" alt="Ass5-ss3" src="https://github.com/user-attachments/assets/81562956-6b07-4a05-b173-8354ab026644" />


---

### Screenshot 4 — Terraform MCP Connection

Add a screenshot showing Terraform MCP connected and available.

Add your screenshot here.

---

### Screenshot 5 — Validation Hooks

Add a screenshot showing the configured Claude Code validation hooks.

<img width="1151" height="319" alt="Ass5-ss5" src="https://github.com/user-attachments/assets/9ac281a7-4386-4c22-aee7-f72068173566" />


---

# Task 1 — Design the Three-Tier Architecture

## Goal

Design the required secure, highly available three-tier architecture and create an architecture diagram before building the infrastructure.

The diagram must show:

- VPC or VNet
- Availability Zones or equivalent availability locations
- Six subnets
- Internet connectivity
- NAT or outbound design
- Public load balancer
- Web Tier
- Internal load balancer
- Application Tier
- Managed MySQL
- Read replica
- Main traffic flow

<<<<<<< HEAD
## Architecture Diagram

Add the completed architecture diagram here.

---

# Task 2 — Build the Terraform Networking and Security Layers
=======


---

#### Screenshot 5 — Public frontend load balancer configuration

<img width="1151" height="319" alt="Ass5-ss5" src="https://github.com/user-attachments/assets/397b0022-2647-4c5d-af0b-6d7b552888d0" />


---

#### Screenshot 6 — Internal backend load balancer configuration

<img width="685" height="334" alt="Ass5-ss6" src="https://github.com/user-attachments/assets/8e706b16-7afd-41b9-beba-ca762e807c7d" />


---

#### Screenshot 7 — Healthy frontend and backend targets or backend pools

<img width="1341" height="447" alt="Ass5-ss7" src="https://github.com/user-attachments/assets/7d56d1fd-dc8a-458e-9b7b-928c0ceab2a1" />


---

# Task 3 — VMs and Application Deployment
>>>>>>> fa0fe3f5940441fa375cf0fca9c1c3c1fc878c30

## Goal

Create the modular Terraform project and implement the network and security layers across the required public and private subnets.

## Evidence

### Screenshot 6 — Modular Terraform Project Structure

Add a screenshot showing the modular Terraform project structure.

<img width="1188" height="389" alt="Ass5-ss8" src="https://github.com/user-attachments/assets/c1f4d4b5-aa7d-4b4a-a545-9a57fd425125" />


---

### Screenshot 7 — Six-Subnet Architecture

Add a screenshot showing the six-subnet architecture across two availability locations.

<img width="1366" height="390" alt="Ass5-ss9" src="https://github.com/user-attachments/assets/60a88893-59d7-4c75-86fa-946489c1180e" />


---

### Screenshot 8 — Public and Private Tier Separation

Add a screenshot showing the public and private tier separation, including routing and security boundaries.

<img width="1348" height="632" alt="Ass5-ss10" src="https://github.com/user-attachments/assets/6102d10c-1d20-400f-8ff6-07a76e7dfccd" />


---

# Task 3 — Build the Load-Balancing and Compute Layers

## Goal

Deploy the public and internal load balancers and the Web and Application compute resources required by the Book Review App.

## Evidence

### Screenshot 9 — Web and Application Compute

Add a screenshot showing the Web and Application compute resources in their required subnets.

<img width="1344" height="600" alt="Ass5-ss11" src="https://github.com/user-attachments/assets/fc6cd83e-dcf3-4104-af76-87cf20c6ddd5" />


---

### Screenshot 10 — Public Load Balancer

Add a screenshot showing the internet-facing public load balancer.

<img width="1343" height="562" alt="Ass5-ss12a" src="https://github.com/user-attachments/assets/2b2361d6-cf5b-4d48-8ddb-9f4e3b32214f" />
<img width="1343" height="657" alt="Ass5-ss12b" src="https://github.com/user-attachments/assets/5845cdb8-4070-4c7d-8c53-28467e9a2732" />


---

### Screenshot 11 — Internal Load Balancer

Add a screenshot showing the private internal load balancer.

<img width="1348" height="591" alt="Ass5-ss13" src="https://github.com/user-attachments/assets/01cd4b91-cdec-4eb2-afd6-983200ceda96" />


---

### Screenshot 12 — Healthy Targets

Add a screenshot showing healthy target groups or backend pools.

<img width="1344" height="610" alt="Ass5-ss14" src="https://github.com/user-attachments/assets/e98e45a1-00a5-4ffb-91dc-4b542ea17447" />


---

# Task 4 — Build the Managed MySQL Database Layer

## Goal

Deploy a private, highly available managed MySQL database with a read replica and restrict database connectivity to the Application Tier.

## Evidence

### Screenshot 13 — Managed MySQL Database

Add a screenshot showing the managed MySQL database deployment.

<img width="1349" height="656" alt="Ass5-ss15" src="https://github.com/user-attachments/assets/2a5167b3-ba80-49e0-88d9-eecc55699cfd" />


---

### Screenshot 14 — High Availability

Add a screenshot showing the Multi-AZ or high-availability configuration.

<img width="1344" height="610" alt="Ass5-ss14" src="https://github.com/user-attachments/assets/b1875a1b-bc71-459d-b2ca-1916d1737c1d" />


---

### Screenshot 15 — Read Replica

Add a screenshot showing the read replica configuration.

<img width="1349" height="656" alt="Ass5-ss15" src="https://github.com/user-attachments/assets/4bcf5127-5d34-4844-a50a-75cecef83fd2" />


---

### Screenshot 16 — Private Database Access

Add a screenshot showing that the database is private and accepts MySQL traffic only from the Application Tier.

<img width="1348" height="563" alt="Ass5-ss16" src="https://github.com/user-attachments/assets/48ec6878-700f-4cf6-a79d-62c3a6791e96" />


---

# Task 5 — Validate, Review, and Apply the Terraform Configuration

## Goal

Validate the Terraform configuration, review the execution plan using both Agentic AI and human judgment, and apply the infrastructure changes only after all required checks pass.

## Evidence

### Screenshot 17 — Terraform Validation

Add a screenshot showing successful `terraform validate` output.

<img width="514" height="195" alt="Ass5-ss17" src="https://github.com/user-attachments/assets/a4aba8c4-7e80-4ad5-939f-a2f0bc0b8e3b" />


---

### Screenshot 18 — Terraform Plan

Add a screenshot showing the Terraform plan output.

<img width="1340" height="680" alt="Ass5-ss18" src="https://github.com/user-attachments/assets/b2358815-3d8b-42ee-a87c-942d1a5428aa" />


---

### Screenshot 19 — Terraform Apply

Add a screenshot showing successful `terraform apply` completion.

<img width="923" height="547" alt="Ass5-ss19" src="https://github.com/user-attachments/assets/7027997d-24fd-412e-bbb5-550514a55f73" />


---

# Task 6 — Deploy and Configure the Book Review Application

## Goal

Deploy and configure the Book Review App across the Web, Application, and Database tiers and verify the complete application functionality.

## Evidence

### Screenshot 20 — Homepage

Add a screenshot showing the Book Review App homepage through the public endpoint.

<img width="1348" height="688" alt="Ass5-ss20" src="https://github.com/user-attachments/assets/0a0c0cb0-63cc-40c9-849a-ef8e7d14d8df" />


---

### Screenshot 21 — Login or Authentication

Add a screenshot showing successful login or authentication.

<img width="1116" height="450" alt="Ass5-ss21" src="https://github.com/user-attachments/assets/8c18ed76-27c2-4b7f-afb7-354eb33b685c" />


---

### Screenshot 22 — Book Data

Add a screenshot showing the book listing or book details.



---

### Screenshot 23 — Review Functionality

Add a screenshot showing the review functionality working successfully.



---

### Screenshot 24 — Backend or API Evidence

Add a screenshot showing that the backend or API is working successfully.

<img width="1366" height="244" alt="Ass5-ss24" src="https://github.com/user-attachments/assets/4d4b0cca-dd14-4a2b-b246-013bb93c7858" />


---

### Screenshot 25 — Database Reads and Writes

Add a screenshot showing successful database reads and writes.



## Public Application URL

**Public Application URL / DNS:** Add the working public application URL or load-balancer DNS here

---

# Task 7 — Demonstrate the Agentic AI Workflow

## Goal

Demonstrate how Claude Code assisted with Terraform generation, architecture and security review, and evidence-based troubleshooting while infrastructure-changing decisions remained under human control.

You do not need to submit your complete Claude Code conversation history. Include only focused evidence.

## Evidence

### Screenshot 26 — AI-Assisted Terraform Generation

Add a screenshot showing one useful example of AI-assisted Terraform generation or improvement.

<img width="1003" height="352" alt="Ass5-ss26" src="https://github.com/user-attachments/assets/9e6f25d5-ca42-4a62-8194-c34a46d7408c" />


---

### Screenshot 27 — Architecture or Security Review

Add a screenshot showing one structured architecture or security review result.

<img width="1245" height="520" alt="Ass5-ss27" src="https://github.com/user-attachments/assets/e2be17e8-ef93-4b14-9696-28c85835bb25" />


---

### Screenshot 28 — AI-Assisted Troubleshooting

Add a screenshot showing one AI-assisted troubleshooting interaction based on collected evidence.



---

# Task 8 — Complete the Final Architecture Review

## Goal

Review the completed infrastructure against the original capstone requirements and resolve significant architecture, security, reliability, and cost issues.

Confirm that the final review covers:

- Tier separation
- Availability
- Public exposure
- Routing
- Security rules
- Load balancing
- Database privacy
- Secrets
- Terraform quality
- Module structure
- Reliability
- Obvious cost risks

Use Screenshot 27 as the focused evidence for the structured architecture or security review.

---

# Task 9 — Answer the Reflection Questions

## Goal

Reflect on the architecture, Terraform implementation, and Agentic AI workflow. Answer each question briefly in your own words.

## Architecture

### 1. Why did you separate the Web, Application, and Database tiers?

The tiers were separated so each layer has a specific responsibility and security boundary. The Web Tier handles public HTTP traffic, the Application Tier handles business logic, and the Database Tier stores persistent data.


### 2. Why is the Application Tier private?

The Application Tier does not need direct internet access from users. Keeping it private prevents users from directly reaching the backend servers and forces traffic through the internal load balancer.

### 3. Why is MySQL private?

The database contains application data and should not be directly accessible from the internet. Only the Application Tier should be able to communicate with MySQL on port 3306.

### 4. Why are multiple Availability Zones used?

Multiple Availability Zones reduce dependence on a single failure location. If one Availability Zone becomes unavailable, resources in the other zone can continue serving traffic.

### 5. What is the difference between Multi-AZ/high availability and a read replica?

Multi-AZ is primarily for availability and failover. A read replica maintains a separate copy that can be used to handle read workloads. They solve different problems: one focuses on availability, while the other can help with read scalability.

## Terraform

### 6. How did you divide your Terraform into modules?

I divided the Terraform configuration into modules for networking, security, load balancing, Web, Application, and Database resources. This keeps each infrastructure layer organized and makes the configuration easier to maintain.

### 7. How do the modules communicate through variables and outputs?

Modules receive configuration through variables and expose resources through outputs. Other modules can then use those outputs to reference things such as subnet IDs, security groups, target groups, and load balancers.

### 8. What did you specifically check in `terraform plan`?

I checked the resources Terraform intended to create or modify, their dependencies, networking relationships, security rules, instance configuration, load balancers, and database configuration before allowing the changes to be applied.

## Agentic AI

### 9. What was the purpose of `CLAUDE.md`?

CLAUDE.md provided project-specific context and safety rules to Claude Code. It defined the required architecture, security boundaries, Terraform expectations, and rules requiring human approval before infrastructure-changing actions.

### 10. What work did the Terraform Engineer subagent perform?

The Terraform Engineer subagent assisted with Terraform structure, resource definitions, module implementation, validation, and infrastructure-related improvements while following the project constraints.

### 11. What did the Architecture and Security Reviewer identify?

The reviewer was used to examine the architecture and security boundaries, including public exposure, tier separation, security-group relationships, database privacy, load balancing, reliability, and potential risks.

### 12. Why did you use Terraform MCP instead of relying only on Claude's existing Terraform knowledge?

Terraform MCP provided project and infrastructure-aware information that could be checked against the actual Terraform environment. This reduced reliance on assumptions and made the AI-assisted workflow more evidence-based.

### 13. What was the purpose of your validation hooks?

The validation hooks provided automated checks before changes were accepted. They helped catch configuration or security problems early and reduced the chance of applying an invalid configuration.

### 14. Describe one real issue Claude helped you troubleshoot.

One real issue occurred when the Book Review homepage did not display the books. Browser developer tools showed a request to /undefined/api/books returning 404. Tracing the request led to the frontend API helper, where an undefined API URL was being combined with /api/books. The API helper was changed to use the same-origin /api path.

### 15. Describe one recommendation you reviewed, modified, or rejected instead of accepting blindly.

One example was the decision not to introduce Docker simply because it was available. The deployed application was already working with Node.js and systemd on EC2, so Docker was not necessary unless it was explicitly required by the capstone specification. The decision was based on the project's actual requirements rather than automatically adding another technology.

---

# Task 10 — Publish the Mandatory LinkedIn Post

## Goal

Publish a LinkedIn post describing the capstone, the technical work completed, the Agentic AI workflow, and the lessons learned.

Write the post in your own words, include at least one project image or other proof, and ensure that it can be viewed by the submission reviewer.

## LinkedIn Post URL


**LinkedIn Post URL:** Add your LinkedIn post URL here





---

#### Screenshot 16 — Published LinkedIn post showing the text and at least one image or proof




---

# Submission Instructions

- Complete Tasks 0–10 in sequence.
- Include all Screenshots 1–28 exactly as specified.
- Ensure that your full name is visible in the required screenshots.
- Include the selected cloud platform.
- Include the completed architecture diagram.
- Include the modular Terraform project structure.
- Include the working public application URL or public load-balancer DNS.
- Include all required Agentic AI workflow evidence.
- Answer all 15 reflection questions briefly in your own words.
- Include the published LinkedIn post URL.
- Do not expose cloud credentials, database passwords, SSH private keys, JWT secrets, access tokens, account IDs, Terraform state containing sensitive values, or other confidential information.
- Review all screenshots and project files carefully before submitting through GitHub.

---

# Completion Checklist

- [ ] Selected AWS or Azure
- [ ] Added and reviewed the Agentic AI starter files
- [ ] Configured `CLAUDE.md`
- [ ] Configured the Terraform Engineer subagent
- [ ] Configured the Architecture and Security Reviewer subagent
- [ ] Connected Terraform MCP
- [ ] Configured validation hooks and safety guardrails
- [ ] Created the architecture diagram
- [ ] Created the six-subnet design
- [ ] Configured public Web Tier routing
- [ ] Kept the Application Tier private
- [ ] Kept the Database Tier private
- [ ] Configured tier-specific Security Groups or NSGs
- [ ] Restricted backend port `3001`
- [ ] Restricted MySQL port `3306` to the Application Tier
- [ ] Created the public load balancer
- [ ] Created the internal load balancer
- [ ] Configured listeners and health checks
- [ ] Deployed the Web Tier compute resources
- [ ] Deployed the private Application Tier compute resources
- [ ] Provisioned private managed MySQL
- [ ] Configured Multi-AZ or high availability
- [ ] Configured a read replica
- [ ] Created the modular Terraform project
- [ ] Used variables, outputs, and module dependencies
- [ ] Used current Terraform documentation through MCP
- [ ] Used hooks for deterministic validation
- [ ] Completed `terraform fmt`
- [ ] Completed `terraform validate`
- [ ] Reviewed `terraform plan`
- [ ] Completed the Terraform Engineer review
- [ ] Completed the Architecture and Security review
- [ ] Applied the infrastructure only after human approval
- [ ] Deployed and configured the backend
- [ ] Deployed and configured the frontend
- [ ] Configured Nginx where required
- [ ] Configured the internal backend endpoint
- [ ] Configured the public frontend endpoint
- [ ] Verified the homepage
- [ ] Verified login or authentication
- [ ] Verified book data
- [ ] Verified review functionality
- [ ] Verified the backend API
- [ ] Verified database reads and writes
- [ ] Verified healthy load-balancer targets
- [ ] Included AI-assisted Terraform generation evidence
- [ ] Included one architecture or security review
- [ ] Included one AI-assisted troubleshooting example
- [ ] Completed the final architecture review
- [ ] Answered all 15 reflection questions
- [ ] Published the mandatory LinkedIn post
- [ ] Added the LinkedIn post URL
- [ ] Captured all 28 required screenshots
- [ ] Confirmed that my full name is visible in the required screenshots
- [ ] Checked that no secrets or sensitive information are exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations through hands-on experience.

---

## Resources

- Book Review App Repository: [https://github.com/pravinmishraaws/book-review-app](https://github.com/pravinmishraaws/book-review-app)
- DMI Official Website: [https://dmi.pravinmishra.com](https://dmi.pravinmishra.com)
- University: [https://university.pravinmishra.com](https://university.pravinmishra.com)
- Discord Community: [https://discord.pravinmishra.com](https://discord.pravinmishra.com)
- Blog: [https://dmi.pravinmishra.com/blog](https://dmi.pravinmishra.com/blog)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra on LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory on LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of the DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
