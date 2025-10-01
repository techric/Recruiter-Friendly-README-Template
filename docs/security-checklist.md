# Security Checklist (Public AWS Portfolio Repos)

## 1) GitHub Repo Settings
- [ ] Visibility: **Public** (for recruiters) — *no secrets committed*
- [ ] **Branch protection** on `main`:
  - [ ] Require pull requests before merging
  - [ ] Require status checks to pass (CI lint/validate)
  - [ ] Block force pushes & branch deletion
  - [ ] Require conversation resolution
  - [ ] (Optional) Require signed commits
- [ ] Disable unused features to reduce spam:
  - [ ] Turn off **Discussions** (if not needed)
  - [ ] Turn off **Issues** (if not needed)
  - [ ] Turn off **GitHub Pages** (if not used)
- [ ] Add **LICENSE** (MIT) and clear **README** scope (demo only)

## 2) Secrets & Files Hygiene
- [ ] **Never** commit access keys, tokens, or `.env`
- [ ] `.gitignore` excludes:
  - [ ] `.env`, `*.pem`, `*.key`, `*.crt`
  - [ ] `.terraform/`, `*.tfstate`, `*.tfstate.*`, `crash.log`
  - [ ] `terraform.tfvars`, `*.auto.tfvars`
  - [ ] `__pycache__/`, `.venv/`, `node_modules/`
  - [ ] `.DS_Store`, `Thumbs.db`
- [ ] If a secret ever lands in git: **rotate the secret** and scrub history

## 3) Security & Analysis (GitHub)
- [ ] Settings → **Security & analysis**:
  - [ ] Enable **Secret scanning**
  - [ ] Enable **Push protection** (block pushes with secrets)
  - [ ] Enable **Dependabot alerts**
  - [ ] (Optional) Enable **Code scanning** (CodeQL)
- [ ] Add `SECURITY.md` (policy + contact)
- [ ] Add `CONTRIBUTING.md` (state you are the sole maintainer)

## 4) GitHub Actions (Safe-by-Default)
- [ ] Actions run **lint/validate only** (no live deploys from public CI)
- [ ] Settings → Actions → General:
  - [ ] **Restrict** to GitHub-verified actions you trust
  - [ ] Require approval for first-time contributors
  - [ ] Disable workflows from **forked PRs** or require explicit approval
- [ ] If you must access AWS from CI:
  - [ ] Use OIDC to assume a **scoped IAM role** (no static keys)
  - [ ] Scope trust policy to this repo (and environment if used)
  - [ ] Start with **plan-only**; apply only by manual approval or locally

## 5) AWS Usage (Sandbox & Cost Guardrails)
- [ ] Use a **sandbox AWS account** (separate from personal/prod)
- [ ] Use **AWS IAM Identity Center (SSO)** locally (no long-lived keys)
- [ ] Create **AWS Budgets** alerts (e.g., $5/month email)
- [ ] Tag all resources via Terraform `default_tags`:
  - [ ] `Project`, `Owner`, `Environment`, `CostCenter`, `Purpose`, `TTLHours`
- [ ] Add a **cleanup** path:
  - [ ] Document `terraform destroy` in README
  - [ ] (Optional) TTL/Janitor job to remove expired resources
- [ ] Prefer smallest sizes (free tier where possible) for demos

## 6) Least Privilege & Service Controls
- [ ] IAM roles/policies are **scoped** (no `AdministratorAccess` for demos)
- [ ] Use **AWS KMS** encryption for S3/DynamoDB where applicable
- [ ] Use **VPC endpoints / AWS PrivateLink** if demonstrating private access
- [ ] Enable **AWS GuardDuty** & **AWS Security Hub** (if demonstrating security)
- [ ] Keep **AWS CloudTrail** on in the sandbox account

## 7) Documentation Signals (for Recruiters)
- [ ] README includes **Cost Note**: deploy → screenshot → **destroy**
- [ ] README has **Architecture** and **Screenshots** sections
- [ ] `SECURITY.md` states: no live creds, demo only, on-demand infra
- [ ] (Optional) `CODEOWNERS` limits who can approve merges (you)

## 8) Operational Hygiene
- [ ] Use branches + PRs (even solo) to keep `main` clean
- [ ] Run `terraform fmt` & `validate` in CI
- [ ] Keep example values **non-functional** (placeholders, not real ARNs/IDs)
- [ ] Review PR diffs for unexpected workflow or permission changes

---

### Quick Copy: Minimal `.gitignore` (Terraform-first)
```gitignore
.terraform/
*.tfstate
*.tfstate.*
crash.log
*.tfvars
*.auto.tfvars
.terraformrc
terraform.rc
.env
*.pem
*.key
*.crt
__pycache__/
.venv/
node_modules/
.DS_Store
Thumbs.db
