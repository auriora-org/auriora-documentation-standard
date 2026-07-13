# AURIORA Documentation Standard

**Document ID:** ADS
**Version:** 1.0.0
**Status:** Normative
**Complements:** AURIORA Engineering Standard (AES)
**Language:** English

## About This Standard

This is the documentation standard for all AURIORA projects. It complements the AURIORA Engineering Standard: AES defines *what* must be documented at each maturity level ([AES Maturity and Release](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/07-maturity-and-release.md)); this standard defines *how* documentation is written, organized and maintained.

This standard defines **quality principles**, not a mandatory document tree. Most of its content is recommendation. The guiding rule, from AES:

> Create enough documentation to understand, continue, test and reproduce the work, but never require documentation whose maintenance costs more than the risk it reduces.

Requirement language (aligned with AES):

- **MUST** — mandatory when applicable (equivalent to `SHALL` in AES).
- **SHOULD** — recommended default; engineering judgment may justify another approach. Skipping a SHOULD requires no documented exception.
- **MAY** — optional.

Where this standard and AES conflict, AES prevails.

---

## 1. Documentation Philosophy

AURIORA documentation is written for the reader who arrives years later — a contributor, manufacturer or user who cannot ask the original author.

- **Documentation supports engineering; it is not a parallel project.** Write what helps someone understand, continue, test or reproduce the work. If maintaining a document costs more than the risk it reduces, delete or merge it.
- **Released documentation is part of the product.** A Released artifact without documentation sufficient to understand, build, test and modify it is incomplete ([AES-PHIL-005](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/01-principles.md)). Prototypes are held to a much lighter bar — see Section 2.
- **Documentation evolves with the project.** A change that alters behaviour, interfaces or procedures SHOULD update the affected documentation in the same change set; for Released, externally consumed interfaces this is a MUST. Documentation updated "later" is documentation that is wrong now.
- **Explain intent, not only implementation.** The code and schematic already say *what*; documentation earns its keep by saying *why*.
- **Concise but complete.** Length is a cost, not a sign of thoroughness.
- **Honest about maturity.** Every repository states its maturity level (Experimental / Active Development / Released) in the README, per [AES-LIFE-001](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/07-maturity-and-release.md#aes-life-001-maturity-declaration).
- **Version controlled.** Documentation lives in the repository next to what it documents, in plain-text formats. Markdown is the canonical source; generated PDFs or sites MUST NOT become canonical.

---

## 2. What a Repository Needs

Every repository normally needs exactly two documentation files:

- `README.md`
- `LICENSE`

**Everything else is conditional** — created only when its content exists and is valuable, never as an empty placeholder:

| File | Create when |
|---|---|
| `docs/design-notes.md` | The project accumulates decisions, open questions, test observations, revision notes or temporary deviations worth keeping. One living document is the norm for Active Development ([AES-REL-004](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/07-maturity-and-release.md#aes-rel-004-living-design-notes)). |
| `docs/interfaces.md` (or standalone specs) | The project exposes interfaces others build against. Mandatory in substance for Released interfaces (the contract must exist somewhere citable). |
| `docs/testing.md` | Test strategy or procedures exist beyond what fits in the README. |
| `CHANGELOG.md` | The repository has tagged releases with consumers. Unreleased experimental repositories need no changelog. |
| `CONTRIBUTING.md` | External contributions are actually expected. |
| `docs/adr/` | The project records formal decision records (Section 8). |

A README MAY contain all documentation for a small repository — including design notes, pinouts and build steps. A dedicated `docs/` directory is needed only when the README would otherwise stop being a readable summary. Do not split information into many files for structure's sake; split when a document stops serving one purpose for one audience.

**One fact, one home.** When the same fact would appear in two documents, keep it where it belongs and link from the other. Duplicated facts diverge, and the wrong copy gets read.

---

## 3. README

The README is the front door — for most readers the only document they ever open. A newcomer MUST be able to tell from the README what the project is, its maturity level, and how to build or use it (or where that is documented).

Recommended shape, adapted freely to the project's size:

- **Overview** — what the project is and does, first paragraph, plain language.
- **Status** — maturity level (Experimental / Active Development / Released), honestly, plus known hazards and critical operating constraints where they exist.
- **Purpose / context** — why it exists; links to related AURIORA standards, modules or interfaces.
- **Usage** — build, flash, install or open instructions, with prerequisites; or a link to the full document if long.
- **Interfaces / pinouts** — where applicable and small enough to live here.
- **Documentation links** — what to read next, when `docs/` exists.
- **License** — name and link.

Small experimental repositories can cover all of this in a screenful. That is the intent, not a shortcut.

---

## 4. Markdown Conventions

Recommendations that keep repositories consistent and diffs clean. None of these require review evidence.

- **Headings:** one `#` H1 per document (the title); don't skip levels; headings are sentence case and unique within the document.
- **Lists:** `-` for unordered, `1.` for ordered; one concept per item; at most two nesting levels.
- **Tables** for genuinely tabular facts (parameters, pinouts), with units in the header. Prose belongs in prose.
- **Code blocks:** fenced with a language tag for anything machine-readable; inline `code` for identifiers, filenames and commands.
- **Notes and warnings:** `> **Note:**` and `> **Warning:**` blockquotes. Reserve warnings for damage, data loss or safety.
- **Links:** descriptive link text, never bare "here"; relative links within a repository.
- **Line discipline:** no hard-wrapped paragraphs at arbitrary columns; no trailing whitespace; files end with a newline.
- **Emphasis** MUST NOT carry normative meaning on its own — requirement keywords do that.

---

## 5. Writing Style

The goal is transfer of understanding with zero ambiguity.

- **Matter-of-fact tone**, respectful of the reader's time. No filler ("simply", "obviously"), no marketing language ("blazing fast" is not a specification).
- **Active voice** — "the bootloader verifies the image", not "the image is verified". The actor matters.
- **Precision:** numbers have units and tolerances; claims are specific and verifiable ("starts within 200 ms", not "starts quickly"); typical vs. guaranteed is stated.
- **Consistent terminology:** one concept, one term — the AES [Terminology](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/02-terminology.md) term where one exists. Readers assume different words mean different things.
- **No ambiguity:** every "it" and "this" has an unmistakable referent; conditions state both branches.
- **International English:** plain vocabulary, no idioms; one spelling convention per repository (US English is the default).

Good grammar matters because broken language ships broken understanding — but there is no separate grammar review stage. Read your own text once before merging; that is the process.

---

## 6. Diagrams and Images

A good diagram replaces a page of prose; a stale one poisons it.

- **Text-based diagram formats first** (Mermaid, PlantUML or equivalent) — they diff, merge, and get updated because updating is cheap. Binary drawing formats: commit the editable source alongside the export.
- **Match the implementation:** state machines use the implementation's state names; signal-flow diagrams use the schematic's signal names. A diagram using different names than the design is a trap.
- **Prefer vector (SVG)** for drawings and plots; PNG for photos and screenshots; JPEG never for anything containing text or fine lines.
- **Name image files descriptively** (`power-tree.svg`, not `image1.png`) in a `docs/images/` directory (or wherever the project keeps assets).
- **Captions and figure numbering** are useful for documents where figures are referenced from distant prose — typically formal interface specs and release documentation. Simple inline figures in a README or design notes need neither.
- **A requirement MUST NOT exist only inside a picture** — normative content is text; diagrams illustrate it.
- Prefer text over screenshots of text: text is searchable, diffable and doesn't age.

---

## 7. Code, Hardware and Interface Documentation

Domain detail lives in the companion guides ([AFSG](https://github.com/auriora-org/auriora-firmware-style-guide) §19, [ASSG](https://github.com/auriora-org/auriora-software-style-guide) §19, [AHDG](https://github.com/auriora-org/auriora-hardware-design-guide) §15). Common rules:

- **Public API that others consume** SHOULD carry documentation comments: what it does, parameters with units and valid ranges, errors, side effects. For Released libraries and protocols this is a MUST — an undocumented public contract is unfinished.
- **Interfaces that cross repository boundaries** (protocols, file formats, connector pinouts, register maps) MUST have a citable specification by Release — the [AES interface contract rules](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/05-interfaces-and-versioning.md) govern the content. Before Release, a current pinout/message table in the README or design notes suffices.
- **Inline comments explain why**, not what: the erratum, the ordering constraint, the reason the obvious approach fails.
- **Document assumptions and known limitations** where a user or maintainer will look for them. "Known and documented" is engineering; "known and unwritten" is a support case.
- **Released hardware** documents what a builder or repairer needs: revision history with compatibility impact, buildable BOM, connector pinouts with pin 1 unambiguous, operating envelope, assembly notes for what an assembler cannot infer.

---

## 8. Decision Records

Most decisions need no record beyond a commit message, an issue or a line in `docs/design-notes.md`. The escalation ladder is defined in [AES Decisions and Governance](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/08-decisions-and-governance.md); in short:

- **Routine judgment** (component choice, layout, refactoring, reversible decisions): no record required. ADRs MUST NOT be demanded for these.
- **Worth remembering** (rejected alternatives, measurement-driven choices): a dated note in `design-notes.md`.
- **Expensive to reverse or sure to be questioned** (platform/MCU selection for a product, protocol design, storage formats, licensing): an ADR is recommended.
- **Platform-wide** (frozen vocabulary, breaking changes to Released interfaces, EEPROM schema majors, family supersession): an EDR is mandatory — see [AES-EDR-001](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/08-decisions-and-governance.md#aes-edr-001-edr-trigger).

When you do write an ADR: `docs/adr/NNNN-short-title.md`, numbered sequentially, one to two pages:

```markdown
# ADR-0001: Decision Title

## Status
Proposed / Accepted / Superseded by ADR-NNNN

## Context
What problem or constraint forced a decision?

## Alternatives Considered
The realistic options with their essential trade-offs.

## Decision
One or two sentences.

## Consequences
What this costs and commits us to.
```

Accepted ADRs are not rewritten; a new ADR supersedes the old one. Write them at decision time — an ADR written months later records a justification, not a decision.

---

## 9. Versioning and Changelogs

- Documentation in a repository describes that branch's current state; released documentation is fixed by the release tag. A release MUST NOT ship documentation describing the previous release for externally consumed interfaces and procedures.
- **Changelog, when the repository has releases:** `CHANGELOG.md` following [Keep a Changelog](https://keepachangelog.com/) — newest first, one section per version with ISO 8601 date, entries grouped under Added / Changed / Deprecated / Removed / Fixed / Security (omit empty ones), written from the consumer's perspective. Every released version corresponds to a tag.
- **Deprecated documents** are marked at the top — status, reason, replacement link — and unlinked from entry points. Superseded content stays reachable through version control; never silently deleted, never left masquerading as current.

---

## 10. File Naming and Cross-References

- Filenames are `kebab-case` (`interface-specification.md`, `power-tree.svg`); conventional names keep their casing (`README.md`, `LICENSE`). Names say what a file *is*, not when it was made — date prefixes only for genuinely chronological series.
- Renaming a published file breaks inbound links: rename deliberately and fix references.
- **Link, don't repeat.** Reference AES rules by requirement ID (`AES-IF-007`) — requirement IDs are stable link targets. Cite external standards with designation and version (`RFC 2119`, `IPC-2221`).
- Cross-repository references pin to a tag or version when the claim depends on one ("as of AES 1.0.0"), because `main` moves.
- Hardware ↔ firmware ↔ software documentation links its counterparts, with exact versions for compatibility claims.

---

## 11. Review and Maintenance

Documentation review is part of ordinary change review — not a separate bureaucracy.

- When reviewing a change (including self-review, per [AES-QA-001](https://github.com/auriora-org/auriora-engineering-standard/blob/main/docs/07-maturity-and-release.md#aes-qa-001-proportionate-review)), check: do the claims match the artifact — pinouts, values, commands, procedures? Do examples actually work? Is affected documentation updated in the same change? That is the whole checklist; there is no separate documentation-impact checklist for every commit.
- **Wrong documentation is worse than none.** Whoever finds outdated content fixes it, files an issue, or marks it deprecated — immediately.
- **Remove duplication on sight**; replace the copy with a link.
- **Keep links valid** when renaming or restructuring; automate link checking in CI where tooling already exists (it is not required).
- **Prune.** Abandoned plans and notes for long-finished migrations are archived or deleted — version control remembers. Every obsolete page dilutes trust in all the others.

---

*AURIORA Documentation Standard 1.0.0 — complements the AURIORA Engineering Standard. Licensed under CC BY-SA 4.0.*
