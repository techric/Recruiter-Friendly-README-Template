# Security Policy

## 1. Purpose
This repository is for demonstration and recruiter review.  
It contains **no live credentials, sensitive data, or production resources**.  
All AWS infrastructure is created and destroyed on-demand in a sandbox account.

## 2. Practices
- No AWS access keys or secrets are stored in this repo.  
- `.gitignore` excludes sensitive files (e.g., `.env`, `.tfstate`).  
- Infrastructure as Code (Terraform) is written for **ephemeral deployments only**.  
- GitHub Actions are limited to linting, formatting, and validation (no live deployments).  

## 3. Reporting
If you notice a security issue in this repository:
- Please open a private discussion or issue on GitHub.  
- Do **not** submit pull requests with executable code from untrusted sources.  

## 4. Disclaimer
These projects are **non-production, demo-only environments**.  
Any cloud resources shown are destroyed immediately after screenshots are taken to avoid costs and risk.


