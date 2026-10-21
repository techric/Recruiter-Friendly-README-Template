# Changelog

All notable changes to this template are recorded here. Versions follow semantic versioning (major.minor.patch):

- Major: the section structure changes, so READMEs built from an older version need rework
- Minor: new optional sections or guidance
- Patch: wording and formatting fixes

The current version is stamped in the hidden guidance comment at the top of README.md, so you can tell which version a project README was built from.

## 2.0.0 - 2026-10-20

### Added
- Recruiter top block: Highlight line plus Stack, Scope, My role, and Last tested.
- Requirements and Constraints section ahead of the decisions.
- Key Decisions and Trade-offs table and a "What I would do differently" line.
- Operations section with monitoring, a failure-handling table, and an optional runbook link.
- Results table with a required "How measured" column and guidance on honest measurement.
- Security section with five specific areas, Cost section with estimation method, and Production Readiness table.
- How to Run It with real commands and pinned versions.
- Status badge backed by docs/templates/infra-checks.yml (terraform fmt, terraform validate, TFLint, Checkov).
- Mermaid architecture diagram as the default.

### Changed
- Guidance moved into hidden comments; screenshot lines stay hidden until the files exist.
- Wording made cloud-neutral (AWS and Google Cloud).

### Fixed
- Heading without a space, duplicate title, broken lettered list, empty Command Output section, and repo structure display.

## 1.0.0 - 2025-10-01

### Added
- Original recruiter-friendly README template.
