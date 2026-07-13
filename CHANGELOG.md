# Changelog

All notable changes to the AURIORA Documentation Standard are documented in this file. Released versions are tagged in version control.

## 1.0.0 - 2026-07-13

First release.

- Documentation philosophy: enough to understand, continue, test and reproduce the work — never more maintenance than the risk it reduces; documentation scaled to the AES maturity model.
- What a repository needs: `README.md` and `LICENSE` always; everything else (`docs/design-notes.md`, `docs/interfaces.md`, `docs/testing.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `docs/adr/`) conditional on its content existing and being valuable. A README may be a small repository's entire documentation.
- The "one fact, one home" principle and a single living `docs/design-notes.md` as the normal home for decisions, open questions, test observations, revision notes and future work.
- README guidance, Markdown conventions, writing style, and diagram/image recommendations.
- Code, hardware and interface documentation rules scaled by maturity.
- Decision records: routine judgment needs no record; a design-notes line for the memorable; an ADR when a decision is expensive to reverse; an AES EDR for platform-wide decisions.
- Versioning, changelog format (Keep a Changelog, for repositories that release), file naming, cross-references and long-term maintenance rules.
- Requirement language aligned with AES (MUST/SHOULD/MAY; a skipped SHOULD needs no documented exception).
- CC BY-SA 4.0 license.
