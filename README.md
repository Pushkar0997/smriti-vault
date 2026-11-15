# Smriti Vault — Cross-Document Commitment & Conflict Ledger

**Smriti Vault (`smriti-vault`)** is an on-device **UGREEN AI NAS (UGOS / Uliya)** orchestration Skill that audits an authorized NAS folder—reconciling PDFs, contracts, invoices, whiteboard/receipt photos, and meeting voice recordings—into a **SHA-256 source-linked Commitment & Conflict Dossier** before any file is modified or written.

Built for the **UGREEN Hackathon 2026 on AI NAS** (*Track: Automate Your Workflow*) and designed for standalone local-first deployment.

---

## Why Smriti Vault?

Independent consultants, researchers, engineering teams, and students store project contracts, receipts, whiteboard photos, and meeting voice memos in shared folders—but costly contradictions (fee changes, voltage/spec mismatches, or shifted deadlines) stay buried across formats.

Unlike cloud RAG chatbots that upload private files, average conflicting facts, or hallucinate missing details, **Smriti Vault**:
- **Runs 100% locally** inside an explicitly authorized UGREEN AI NAS directory (`target_folder`).
- **Assigns a 5-state epistemic taxonomy** to every claim: `CONFIRMED`, `CONFLICTING`, `SUPERSEDED`, `UNVERIFIED_MENTION`, or `MISSING_IN_SCOPE`.
- **Cross-checks visual scans twice** (`vision-ocr` + `vision-vlm` at temperature `0`), flagging disagreements as `UNCERTAIN_OCR`.
- **Preserves SHA-256 fingerprints** and exact page/timestamp coordinates for every claim.
- **Enforces strict approval gates** (`waiting_approval`)—never deleting, moving, or overwriting original files.

---

## Architecture & Uliya Agent Orchestration

`smriti-vault` is a pure-Markdown declarative parent Skill (`SKILL.md` + `references/`) adhering to the **Uliya Skill Development Standard** (`uliya-skill-kit` v0.7.3, capability catalog v2.0.0). It delegates sequentially to four registered UGOS expert agents:

| Step | Expert Agent | Capabilities Used | Role |
| :--- | :--- | :--- | :--- |
| **1. Inventory & Hashing** | `file-agent` | `ug-filesystem` (`find`, `ls`, `stat`, `sha256sum`), `ug-filemgr` (`duplicate-scan`) | Bounded discovery (<=50 docs, <=20 images, <=3 audio) & SHA-256 deduplication |
| **2. Visual & OCR Pass** | `photo-agent` | `ug-photo` (`meta`, `vision-ocr`, `vision-vlm`) | EXIF timestamps & dual-pass OCR/VLM at `temperature=0` |
| **3. Audio Transcription** | `knowledge-agent` | `ug-knowledge` (`audio-transcription`) | Verbatim on-device voice-note transcription with timestamps |
| **4. Reconciliation** | `document-agent` | `ug-document` (`extract`, `qa`, `reconcile`) | Claim extraction & cross-source contradiction detection |
| **5. Review Preview** | `knowledge-agent` | `ug-knowledge` (`collect-evidence`), `ug-document` (`writing`) | Formats Conflict Dossier & displays exact approval pop-up count |
| **6. Approved Save** | `knowledge-agent`, `file-agent` | `ug-knowledge` (`save-text`), `ug-filemgr` (`tag-add-file`) | Writes new Markdown dossier & applies `smriti-audited` tag only after approval |

---

## Repository Structure

```text
smriti-vault/
├── SKILL.md                        # Uliya parent orchestration Skill
├── references/
│   ├── evidence-contract.md        # 5-state epistemic taxonomy & prompt-injection defense
│   ├── output-template.md          # YAML frontmatter & dossier section schema
│   ├── validation-plan.md          # 2 core test cases + 1 adversarial edge case
│   └── disclosures.md              # Authorship, third-party & AI assistance disclosures
├── LICENSE
├── .gitignore
└── README.md
```

> **Packaging Note for UGREEN Skill Kit (`check-skill.mjs`)**: When packaging `smriti-vault.zip` for UGOS / Uliya submission, include only `SKILL.md` and `references/` inside the `smriti-vault/` skill directory (do not bundle `README.md`, `LICENSE`, or scripts inside the Skill ZIP).

---

## Validation Status & Roadmap

- **Round 1 Status**: Pure-Markdown Uliya Skill package (`smriti-vault.zip`) and 410-word Round 1 Proposal PDF complete. Runtime execution on a physical UGREEN AI NAS iDX6011 Pro is pending Round 2 finalist hardware access.
- **Post-Hackathon Product Roadmap**: Package the 5-state reconciliation engine as a standalone Dockerized local-first B2B/prosumer vault (`FastAPI` + `SQLite` + `Ollama` / `Gemma 4`) for agencies, legal/audit teams, and self-hosted NAS users.

---

## License

MIT License — see [LICENSE](LICENSE) for details.
