# Dossier Output Template & Approval Preview Layout

This reference defines the exact Markdown structure produced by `smriti-vault` in Step 5 (`knowledge-agent`) and written to `{target_folder}/Smriti_Commitment_Dossier_{YYYY-MM-DD}.md` in Step 6 after explicit user and platform approval.

## 1. Dossier Header & Scope Summary

Every generated dossier begins with deterministic YAML frontmatter so UGOS local search tools can index it immediately:

```markdown
---
skill: smriti-vault
schema_version: 1.0.0
target_folder: "<exact_authorized_path>"
audit_focus: "<user_specified_focus>"
files_scanned: <integer>
conflicts_found: <integer>
missing_refs_found: <integer>
---
```

## 2. Section Layout

### Section A: Scope & Integrity Inventory
A Markdown table listing every inspected file inside `target_folder`:
- **Columns**: `File Relative Path` | `Type` | `Size (KB)` | `Modified Date` | `SHA-256 (12-char prefix)` | `Read Status` (`READ`, `DUPLICATE_SKIPPED`, `INACCESSIBLE`).

### Section B: Verified Commitments Ledger (`CONFIRMED` & `SUPERSEDED`)
A structured table of all verified obligations, deadlines, monetary figures, and technical specs:
- **Columns**: `ID` | `Category` | `Extracted Claim / Value` | `Effective Date / Deadline` | `Status` | `Source File & Page/Timestamp` | `Verbatim Quote`.

### Section C: Cross-Document Conflict Dossiers (`CONFLICTING`)
For each contradiction detected across documents, photos, or transcripts:
- **Conflict ID & Topic**: Clear title of the disputed parameter (for example, `CF-01: Milestone 2 Delivery Date`).
- **Source A vs. Source B**: Side-by-side comparison showing exact file paths, SHA-256 prefixes, page numbers or audio timestamps, and verbatim quotes.
- **Resolution Question**: One concrete question for the human reviewer to settle the discrepancy.

### Section D: Evidence Gap Planner (`MISSING_IN_SCOPE` & `UNVERIFIED_MENTION`)
Lists every external annex, receipt, or configuration file referenced by a document in scope that was not found inside `target_folder`, plus any uncorroborated voice-memo or low-confidence OCR claims, paired with the single highest-value verification step to close the gap.

## 3. Pre-Write Approval Banner

Before transitioning to Step 6 (`waiting_approval`), the Skill displays a concise summary block:
- **Target New File**: `{target_folder}/Smriti_Commitment_Dossier_{YYYY-MM-DD}.md`
- **Destructive Actions**: `0 deletes, 0 moves, 0 overwrites` (originals remain untouched).
- **Expected Platform Pop-ups**: `1 approval prompt` for `ug-knowledge save-text` (plus `1 approval prompt` if optional `smriti-audited` batch tagging is requested).
