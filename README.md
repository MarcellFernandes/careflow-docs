# CareFlow API Documentation — Technical Writing Portfolio

## Project Overview

This repository contains a fictional healthcare API documentation project created as part of a technical writing portfolio. The purpose is to simulate production-style REST API documentation, demonstrating clarity, structure, consistency, and developer-focused communication.

The CareFlow API represents a platform that connects home care organizations with licensed healthcare professionals. While fictional, the documentation is intentionally designed to reflect real-world SaaS API standards and workflows.

---

## Skills Demonstrated

This project showcases:

- REST API documentation design
- Consistent JSON schema modeling
- Authentication documentation
- Error handling documentation
- CRUD resource documentation
- Developer onboarding flows
- Command-line integration examples (cURL)
- Documentation structure and navigation design
- MkDocs static site generation

The goal is to demonstrate how complex technical systems can be documented clearly for developers and stakeholders.

---

## Documentation Structure

The documentation site includes:

- Overview and API philosophy
- Authentication flows
- Professionals resource modeling
- Error handling guidance
- Quickstart onboarding guide
- Practical cURL integration examples

All content is written to simulate production-grade API documentation.

---

## Quick Start (Local Preview)

Recommended: use a Python virtual environment.

```bash
python -m venv .venv
.venv\Scripts\activate
pip install --upgrade pip
pip install mkdocs mkdocs-material
```

Start the local documentation server:

```bash
python -m mkdocs serve
```

Open:

```
http://127.0.0.1:8000
```

in your browser.

---

## Build Static Site

To generate the static documentation site:

```bash
python -m mkdocs build
```

The output will be created in the `site/` directory.

---

## Windows PowerShell Notes

Activate the virtual environment:

```powershell
.\.venv\Scripts\Activate.ps1
```

If script execution is restricted:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
```

---

## Troubleshooting

- Missing theme error → install `mkdocs-material`
- Navigation errors → verify `mkdocs.yml` references existing files in `docs/`
- Port already in use → change port:

```bash
python -m mkdocs serve --dev-addr 0.0.0.0:8080
```

---

## Optional: Requirements File

To reproduce the environment:

Create `requirements.txt`:

```
mkdocs
mkdocs-material
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Purpose

This project exists purely as a portfolio demonstration of technical writing practices applied to API documentation. It emphasizes clarity, structure, consistency, and developer usability — key skills for professional documentation roles.

---

Built as a technical writing portfolio project.
