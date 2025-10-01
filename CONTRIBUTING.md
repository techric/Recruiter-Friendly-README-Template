# Contributing

This repository is a **public, recruiter-facing AWS demo/template**. It exists to showcase design, Infrastructure as Code (IaC), documentation, and proof-of-work screenshots. **I am the sole maintainer**; external pull requests are not accepted. If you have suggestions, please open an Issue.

- **No live infrastructure is kept running**. Projects are deployed on-demand for screenshots, then destroyed to avoid costs.
- **No secrets** (keys, tokens, `.env`) may be committed. See `SECURITY.md` and `docs/security-checklist.md`.

---

## How to Propose Changes (for non-maintainers)

- Open a **GitHub Issue** describing:
  - **What’s wrong / missing**
  - **Proposed fix or improvement**
  - (Optional) Links or references
- **Do not** include any sensitive info (accounts, ARNs, IDs, keys).

> External PRs will be closed; please use Issues for suggestions.

---

## Maintainer Workflow (for my own changes)

1. Create a branch: `feature/<short-name>` or `fix/<short-name>`.
2. Run local checks:
   - `terraform fmt` and `terraform validate` (if Terraform present)
   - Lint any scripts/code as applicable
3. Sanity checks before commit:
   - No credentials or `.env` files staged
   - README includes a **Cost Note** (deploy → screenshot → destroy)
   - Update docs/diagrams if architecture changed
4. Commit style (recommended):
   - `feat(iac): add vpc module`
   - `fix(docs): correct checklist path`
   - `chore(ci): add terraform validate`
5. Open a PR into `main`:
   - Ensure CI checks pass (lint/validate only; no live deploys)
   - Squash & merge after review

---

## CI/CD Policy (Public Repo Safety — GitHub Actions & GitLab CI)

**Goal:** CI runs *safe* checks (lint/validate/plan) only. No live cloud deploys from public pipelines.

### Common Rules (both platforms)
- Pipelines run **lint/format/validate** (and optionally **plan**) only.
- **Never** store long-lived cloud keys in CI variables. If deployment is ever needed, use **OIDC** to assume a **scoped IAM role** at run time.
- Jobs that could change infrastructure must require **maintainer approval** and run only on **protected branches/environments**.
- **Forked PR/MR pipelines** must not execute privileged jobs without **explicit maintainer approval**.
- Prefer **trusted runners** (self-hosted/group-scoped). Avoid executing privileged jobs on public/shared runners.
- Keep artifacts to basics (logs, plans). No secrets in artifacts.

### GitHub Actions
- **Settings → Actions → General**
  - Restrict to **GitHub-verified actions** you trust.
  - **Require approval** for first-time contributors.
  - (Recommended) Disable workflows from forks or require manual approval before they run.
- Use the `id-token: write` permission and `aws-actions/configure-aws-credentials` **only** for plan-level jobs.
- Example safe workflow scope:
  - `terraform fmt` / `validate` (always)
  - `terraform plan` (manual `workflow_dispatch` only)
  - **No `apply`** from public CI.

### GitLab CI
- **Settings → CI/CD → Runners**
  - Disable **shared runners** for privileged jobs; use **specific/group runners** with tags.
- **Settings → CI/CD → Variables**
  - If variables are needed, mark them **Masked** and **Protected**; scope to **protected branches** only.
  - Prefer OIDC to assume a scoped role; do **not** store static keys.
- **Settings → General → Visibility, project features, permissions**
  - Disable **Public pipelines** for external forks, or require **maintainer approval**.
- **MR pipeline rules**
  - Run pipelines **only for merge requests** (e.g., `workflow: rules`) and require **maintainer approval** for MR pipelines from forks.
- Example safe `.gitlab-ci.yml` (validate only):
  ```yaml
  stages: [validate]

  validate:
    image: hashicorp/terraform:1.6
    stage: validate
    script:
      - terraform -chdir=infra/terraform/envs/dev init -backend=false
      - terraform -chdir=infra/terraform/envs/dev fmt -check
      - terraform -chdir=infra/terraform/envs/dev validate
    rules:
      - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      - if: '$CI_COMMIT_BRANCH == "main"'
        when: always


---

## Security & Reporting

- Read **`SECURITY.md`** (policy) and **`docs/security-checklist.md`** (actions).
- If you believe you found a security issue:
  - Open a private Issue or contact the maintainer via GitHub.
  - Do **not** include exploits or secrets; provide high-level details.

---

## License

This project is licensed under the **MIT License** (see `LICENSE`). Attribution appreciated but not required.

---

## Code of Conduct (Short)

Be respectful and constructive. Spam, harassment, and off-topic content may be removed.
