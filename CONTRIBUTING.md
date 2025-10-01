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

## CI/CD Policy (Public Repo Safety)

- GitHub Actions run **lint/validate/plan** only. **No applies** to AWS from public CI.
- If a plan is enabled, it requires **manual approval** and is run by the maintainer.
- Workflows from forks require explicit maintainer approval.

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
