# Security Policy — Not-Humans-Lab (umbrella)

This is the org-wide policy. If you know which sub-project (daily-dose, nh-deck, nh-skills) a vulnerability affects, report it there instead once that repo exists — this file exists for reporters who don't know which one, or for issues that span more than one.

## Supported Versions

No releases exist yet for any sub-project. This section will be filled in with a version table once the first release ships.

## Reporting a Vulnerability

Please report privately — do not open a public issue for a security concern. Use GitHub's private vulnerability reporting on the relevant repo once it exists, or contact the maintainer directly. We aim to acknowledge reports within a best-effort window (no formal SLA yet at this stage of the project).

## Disclosure Policy

Coordinated disclosure: please give us a reasonable window to investigate and fix before any public disclosure. Credit is given to reporters who request it.

## Scope

In scope: the code and infrastructure of daily-dose, nh-deck, nh-skills, and this umbrella repo, once they exist. Out of scope: third-party dependencies (report upstream) and social-engineering/physical-security issues.

## Secrets Handling

No secrets are ever committed to any repo in this suite. All API keys (LLM providers, etc.) live in environment variables or platform-native secret stores (GitHub Encrypted Secrets, Vercel env vars) — never hardcoded, never logged.

## Supply Chain / Dependency Policy

Each sub-project pins its dependencies and will run automated dependency scanning once scaffolded. nh-skills specifically will carry a supply-chain integrity policy (SHA-256 manifests, provenance across promotion stages) as its primary security concern, since its distributed artifacts are the thing being trusted by consumers.

## Per-Project Routing Table

*(empty — filled in as each sub-project gets its own `SECURITY.md`)*

| Project | Own SECURITY.md |
|---|---|
| daily-dose | not yet scaffolded |
| nh-deck | not yet scaffolded |
| nh-skills | not yet scaffolded |

## Contact

To be added once a dedicated security contact channel is set up for the Not-Humans-Lab org.
