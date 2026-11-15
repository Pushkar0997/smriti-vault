# Authorship, Third-Party Components & AI Assistance Disclosures

This file provides all required disclosures under the UGREEN Hackathon 2026 Official Rules and the Uliya Skill Development Standard.

## 1. Originality & Principal Functionality Developed for This Hackathon

- **Entrant & Author**: Pushkar Kumar (`Pushkar0997`).
- **New Development Declaration**: `smriti-vault` (`SKILL.md` and all four files in `references/`) was newly conceived, architected, and written during the UGREEN Hackathon 2026 submission period (November 2026) specifically for the UGREEN AI NAS (UGOS / Uliya) ecosystem.
- **Prior Conceptual Inspiration**: The entrant previously developed standalone web/desktop projects (`Pushkar0997/Smriti` for student RAG study notes, `Pushkar0997/RepoBridge` for repository context extraction, and `Pushkar0997/ai-notetaker` for local audio note-taking). No code, scripts, binaries, or prior submission materials from those repositories are bundled or reused in this Skill package; `smriti-vault` is a pure-Markdown multi-agent UGOS orchestration Skill designed from scratch around UGREEN's native expert agents (`file-agent`, `photo-agent`, `document-agent`, `knowledge-agent`).

## 2. Third-Party Components & Open-Source Licenses

- **Embedded Third-Party Code or Libraries in Skill ZIP**: **None**. This Skill package consists strictly of 5 UTF-8 Markdown files (`SKILL.md` and 4 files under `references/`). It contains zero executables, zero shell/Python/JS scripts, zero binary weights, and zero external API calls.
- **Platform Specification Referenced**: UGREEN Skill Developer Package (`uliya-skill-kit` v0.7.3) and UGREEN Public Capability Catalog (v2.0.0), copyright America UGREEN Limited, used under the official UGREEN Hackathon 2026 terms.
- **Local Document Rendering Tools (Used Outside the Skill ZIP for Proposal PDF Generation)**:
  - Python 3.12 (PSF License) — used locally to package the ZIP archive and verify word counts.
  - Chromium / Selenium WebDriver (Apache-2.0 / BSD-3-Clause) and `pypdf` / `pypdfium2` (BSD-3-Clause / Apache-2.0) — used locally to compile and inspect the Round 1 Project Proposal PDF (`UGREEN_Round1_Proposal_Smriti_Vault.pdf`).

## 3. AI Tools Used During Development

- **AI Assistant Disclosure**: Gemini (Google) was used under the entrant's direct supervision to audit the entrant's existing GitHub portfolio, structure the Uliya multi-agent delegation workflow against the UGREEN capability catalog v2.0.0, draft the Markdown reference specifications, and format the Round 1 Project Proposal PDF within the 500-word limit. The entrant defined the target problem, evidence taxonomy, safety gates, and validation scenarios, and reviewed all final submission materials.
- **Runtime AI Model Execution**: At runtime on a UGREEN AI NAS, `smriti-vault` invokes only the local/native UGOS expert agents (`file-agent`, `photo-agent`, `document-agent`, `knowledge-agent`) and makes zero external third-party LLM API calls.
