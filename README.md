# Recruiter-Friendly-README-Template
##Hands-On Projects Worthy of Recruiter Review
# [Project Title Here]

> One-liner about what this AWS project does (example: "Observability on AWS EKS with Prometheus, Loki, and Grafana").

---

## 1. What This Project Shows
- [ ] Problem: (short statement — e.g., "Enterprises lack unified observability across workloads.")
- [ ] Solution: (short statement — e.g., "Deployed PLG stack on AWS EKS using Terraform.")
- [ ] Impact: (short statement — e.g., "Improved incident visibility, reduced MTTR by 40%.")

---
## 2. How to Use This Template
a. **Deploy once** (small/dev resources) → validate it works.
b. **Take 2–3 screenshots** (AWS Console, Grafana, AWS Athena/queries, AWS QuickSight charts) and save them in `docs/screenshots/`.
c. **Add an architecture diagram** to `docs/architecture.png`.d. **Destroy the infra** to avoid charges (`terraform destroy`).
d. Fill in the sections below (What This Shows, Architecture, Screenshots, Tech Used).
e. Link your security docs: 🔐 [Policy](SECURITY.md) • [Checklist](docs/security-checklist.md).

---
## 2. Architecture
High-level diagram of how services fit together.
NOTE: Replace this image with your diagram.
![Architecture](docs/architecture.png)

---

## 3. Screenshots (Proof of Work)
Once the project is deployed, add 2-3 proof screenshots when you deploy once: 

a. **AWS Console**  
   _Example: EKS cluster deployed_  
   ![EKS Screenshot](docs/screenshots/eks-cluster.png)

b. **Grafana Dashboard / AWS Athena Query / AWS QuickSight Chart**  
   _Example: Cost optimization dashboard_  
   ![Dashboard Screenshot](docs/screenshots/dashboard.png)

c. **Command Line Output**  
   _Example: Terraform apply success_  
   
---

## 4. Tech Used
AWS Services (EC2, S3, IAM, etc.), Terraform, GitHub Actions, Python  

---

## 5. Cost Note
This project is created on-demand and destroyed after screenshots are taken to avoid AWS charges.  

Security: [Policy](SECURITY.md) • [Checklist](docs/security-checklist.md)
---

## 6. Repo Structure
/infra       -> Terraform code  
/docs        -> Architecture diagrams & screenshots  
/scripts     -> Helper scripts  
/README.md   -> Project description  
/SECURITY.md -> Security policy
/CONTRIBUTING.md -> Contribution rules (you as a sole maintainer)

   
   Apply complete! Resources: 12 added, 0 changed, 0 destroyed.
