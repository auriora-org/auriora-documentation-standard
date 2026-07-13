# AURIORA Documentation Standard

The AURIORA Documentation Standard (ADS) defines how documentation is written, organized and maintained across AURIORA repositories. It complements the AURIORA Engineering Standard (AES): AES defines *what* must be documented at each maturity level, ADS defines *how*.

ADS defines **quality principles without forcing a document tree**. Every repository normally needs only `README.md` and `LICENSE`; everything else — design notes, interface specs, changelogs, ADRs — is created only when its content exists and is valuable. A README may be the entire documentation of a small repository.

Read the standard: [STANDARD.md](./STANDARD.md)

## Scope

- Documentation philosophy: enough to understand, continue, test and reproduce — never more maintenance than the risk it reduces
- Conditional documentation set: what to create and when, including the single living `docs/design-notes.md`
- README guidance, Markdown conventions, writing style, diagram and image recommendations
- Code, hardware and interface documentation rules, scaled by maturity
- Decision records: when a note suffices, when an ADR is worth writing, when AES requires an EDR
- Versioning, changelog format (Keep a Changelog, for repositories that release), naming, cross-references and maintenance

## Requirement Language

Aligned with AES:

- `MUST` — mandatory when applicable (equivalent to `SHALL` in AES)
- `SHOULD` — recommended default; engineering judgment may justify another approach, no documented exception needed
- `MAY` — optional

Where ADS and AES conflict, AES prevails.

## Versioning and Changes

Released versions are recorded in the [CHANGELOG](./CHANGELOG.md) and tagged in version control.

## License

This documentation is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0)](./LICENSE).
