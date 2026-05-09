# ACI Skydiving Framework

**Working Group drafting workspace for the National Framework for Civilian Skydiving Dropzone Operations in India.**

This repository is the **canonical source of truth** for the Framework drafted by the Aero Club of India (ACI) Skydiving Working Group.

> ⚠️ **Status:** Internal WG draft. Not a regulatory instrument. Not for external circulation.

---

## What's here

| Path | Contents |
|---|---|
| `framework/india_skydiving_framework.md` | The canonical Framework document |
| `annexes/` | Application forms, inspection scorecards, and other supporting artifacts |
| `decisions/` | Architecture Decision Records (ADRs) — one per contested WG decision |
| `meeting-notes/` | Dated WG meeting minutes |
| `.github/` | Pull-request templates, issue templates, and automation |
| `CONTRIBUTING.md` | **How to contribute — read this first** |
| `SCRIBE_PROCESS.md` | How non-tech feedback is converted into PRs |
| `CODEOWNERS` | Required reviewer rules |

---

## How this works (one-paragraph version)

The Markdown files in `framework/` and `annexes/` are the single source of truth. Every change is made through a Pull Request. The `main` branch is protected — nothing reaches `main` without the WG Chair's review and at least one other WG member's approval. Non-tech WG members review a Google Docs mirror of the latest `main` and submit feedback through a structured Google Form; a designated WG Scribe converts that feedback into PRs.

For the full process, see **[CONTRIBUTING.md](./CONTRIBUTING.md)**.

---

## Quick links

- [Contributing guide](./CONTRIBUTING.md)
- [Scribe process](./SCRIBE_PROCESS.md)
- [Decision Records](./decisions/)
- Google Doc mirror (read-only): _[link to be added once Action is set up]_
- WG feedback form: _[link to be added]_

---

## Roles

| Role | Members | Surface |
|---|---|---|
| **Maintainer** (merge gatekeeper) | Abhishek (WG Chair) | GitHub |
| **Tech contributors** | VC-Ops, Member-Training, Member-Equipment, Member-Regulatory | GitHub PRs |
| **Scribe** | Designated Secretariat member | GitHub PRs (on behalf of others) |
| **Non-tech reviewers** | Chair, VC-Safety, Member-Medical, Member-Insurance, Athlete Rep | Google Doc + Form |

---

## Versioning

Milestones are tagged: `v0.2`, `v0.3`, `v0.5`, `v0.9`, `v1.0`. Each tag triggers a release with PDF + Word + Markdown bundle attached.

Current draft: **v0.2**.

---

## License & confidentiality

This repository is private. Do not share contents externally. Final published Framework will carry an ACI license to be determined at v1.0.

---

_For questions, open a [GitHub Issue](../../issues) or contact the WG Chair._
