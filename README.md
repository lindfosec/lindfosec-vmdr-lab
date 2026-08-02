# LindfoSec — Hybrid VMDR Lab

A self-built vulnerability management lab simulating a real international company, built to learn Vulnerability Management the way an actual analyst would: hands-on, with real findings, real troubleshooting, and real remediation — not just theory.

## About

LindfoSec is a fictional company with 5 departments (IT/Management, Finance, HR, Sales & Marketing, R&D), built across a genuinely hybrid environment: 4 AWS EC2 instances and 1 real on-prem Windows endpoint, fully managed and monitored through **Qualys VMDR**.

This project was built as hands-on preparation for an entry-level **Vulnerability Management Analyst** role, pairing formal certifications with a real, working environment.

## Architecture

| Department | Platform | OS | Access |
|---|---|---|---|
| IT / Management | AWS EC2 | Ubuntu | AWS SSM (no SSH, no inbound ports) |
| Finance | AWS EC2 | Amazon Linux | AWS SSM |
| HR | AWS EC2 | Ubuntu | AWS SSM |
| Sales & Marketing | AWS EC2 | Ubuntu | AWS SSM + public HTTPS (443 only) |
| R&D | On-premises | Windows | Direct Qualys Cloud Agent install |

- No SSH access anywhere — all cloud management via AWS Systems Manager, authenticated through IAM roles
- Qualys Cloud Agent deployed across three different package formats (.deb, .rpm, Windows installer)
- Custom Qualys Configuration Profile built and applied via tag-based scoping
- Deliberate least-exposure design — only Sales & Marketing has any inbound access, and only on port 443

## What this project demonstrates

- **End-to-end deployment**: launching infrastructure, securing access, and onboarding assets to Qualys VMDR
- **Real vulnerability remediation**: investigated and fixed a real CVE (CVE-2026-9545, curl) with full before/after verification
- **Honest lifecycle tracking**: correctly identified and documented a "patch not yet available upstream" scenario for wget and OpenSSH — later confirmed resolved once the vendor published the fix
- **Risk-based prioritization**: reasoned through CVSS, exploitability, and network exposure to correctly prioritize findings — independently reconstructing the logic behind Qualys TruRisk
- **Real troubleshooting**: documented genuine issues and fixes, including PowerShell elevation errors, S3 presigned URL handling, and Qualys on-demand scan timing quirks

## Key documentation

- [`docs/Lindfosec-Phase1_Summary.pdf`](docs/Phase1_Summary.pdf) — initial architecture and asset group design
- [`docs/ConfigProfile_and_ITMgmt_Findings.pdf`](docs/ConfigProfile_and_ITMgmt_Findings.pdf) — Configuration Profile build and first real findings review
- [`docs/Lindfosec-First_Remediation_Cycle_HR_curl.pdf`](docs/First_Remediation_Cycle_HR_curl.pdf) — full detect-to-verify remediation cycle
- [`docs/SSM_S3_CloudAgent_Deployment_Reference.pdf`](docs/SSM_S3_CloudAgent_Deployment_Reference.pdf) — deployment methodology reference

*(Full list added as documents are uploaded.)*

## Background

Career changer transitioning into cybersecurity since 2024. Técnico Superior en Seguridad Informática, ISC2 Certified in Cybersecurity, Google Cybersecurity Professional Certificate, Qualys VMDR certification in progress.

[LinkedIn](https://www.linkedin.com/in/eunicechibuike)
