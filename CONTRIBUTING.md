# Contributing to the ACI Skydiving Framework

This document explains how to propose, review, and merge changes to the Framework. It is the operating manual for the Working Group.

There are **two paths** depending on whether you use GitHub:

1. **[Path A — GitHub-comfortable members](#path-a--github-comfortable-members)** — direct PRs.
2. **[Path B — Non-tech members](#path-b--non-tech-members)** — review the Google Doc, submit a Google Form; the Scribe converts your feedback to a PR.

Both paths produce the same result: a tracked, attributed change with full audit trail.

---

## Ground rules (everyone)

1. **No edits go to `main` directly.** Every change is a Pull Request.
2. **Every PR must reference a section number** of the Framework (e.g., `§2A.4.1`, `§3.11`).
3. **Every PR must classify itself**: Correction / Addition / Deletion / Restructure.
4. **Every PR must give a rationale.** "Because USPA says so" is not a rationale; "USPA SIM 5-2.E para 4 specifies a 30 m clearance, our draft says 25 m, recommend aligning" is.
5. **Contested decisions become ADRs.** If a PR will alter a Mandatory standard, it must link to or create a Decision Record in `decisions/`.
6. **The Chair (Abhishek) is the final merger.** No exceptions.

---

## Path A — GitHub-comfortable members

### One-time setup

1. Get added to the repo as a Collaborator (ask the Chair).
2. Sign in to GitHub.
3. (Recommended) Install [GitHub Desktop](https://desktop.github.com/) if you prefer not to use the command line.

### To propose a change

You can do all of this in the GitHub web UI — no command line required.

1. **Open the file** in `framework/india_skydiving_framework.md`.
2. Click the **pencil icon** (top right of the file view) to edit.
3. Make your change. Use Markdown formatting consistent with the existing document.
4. Scroll to the bottom: **"Propose changes"** section.
5. Write a clear commit message: section reference + change in 60 chars.
   - Good: `§2A.4.1: tighten PLA minimum to 320m at Tier 1`
   - Bad: `update`
6. Select **"Create a new branch for this commit and start a pull request"**.
7. Branch name format: `proposed/<section>-<short-desc>`. Example: `proposed/2a4-pla-dimensions`.
8. Click **"Propose changes"**.
9. On the new-PR screen, fill in the PR template completely. Don't skip fields.
10. Click **"Create pull request"**.

### What happens after you open the PR

- The Chair (Abhishek) is auto-assigned as a required reviewer (via `CODEOWNERS`).
- Add at least one other WG member as a reviewer.
- Reviewers leave **line-level comments**.
- You address comments by editing the same branch (commits append to the open PR).
- Once you have **2 approvals (one being the Chair)** and all conversations are resolved, the Chair merges using **"Squash and merge"**.
- The branch is auto-deleted after merge.

### When in doubt

- **Small typo / wording fix** → just open the PR.
- **Anything that changes a Mandatory `[M]` standard** → open an Issue first to discuss; if consensus emerges, then PR with a linked ADR.
- **Adding a new section or restructuring** → open an Issue first; the Chair will route to the relevant sub-group.

---

## Path B — Non-tech members

You don't need a GitHub account. You don't need to use Git.

### Your workflow

1. **Read the latest draft** in the [Google Doc mirror](_link-to-be-added_). It updates automatically when changes are merged.
2. **For comments and discussion:** use the Google Doc's comment feature freely.
3. **For proposed changes** (text you want added, removed, or changed): submit the [WG Feedback Form](_link-to-be-added_).

### What the Form asks you for

The Form has 6 short questions:

1. **Your name and WG role.**
2. **Section reference** (e.g., `§2A.4.1` or "Part 3 SOPs").
3. **Type of change**: Correction / Addition / Deletion / Question / Disagreement.
4. **Current text** (copy-paste the sentence/paragraph you're commenting on, if applicable).
5. **Proposed text or change** (what you want it to say, or what you want to flag).
6. **Why** (rationale, source, or concern).

That's it. Submit.

### What happens to your submission

- The Form populates a Google Sheet that the **Scribe** monitors.
- The Scribe triages: clarification needed → comes back to you; clear change → opens a PR on GitHub on your behalf, attributing the suggestion to you in the PR description.
- The PR follows the normal review process (Path A from this point onward).
- You'll be notified by email when the PR is opened, when it's reviewed, and when it's merged or rejected.
- All your submissions are preserved in the Sheet permanently — even those that don't become PRs — so the audit trail is complete.

### If you change your mind or want to add detail

Just submit another Form with the same section reference; the Scribe will link your submissions together.

---

## Branch naming conventions

| Branch type | Format | Example |
|---|---|---|
| Proposed change | `proposed/<section>-<desc>` | `proposed/2a4-pla-dimensions` |
| Sub-group draft | `subgroup/<group>/<part>` | `subgroup/training/part4` |
| Scribe-raised PR | `scribe/<member>-<section>` | `scribe/medical-2a7` |
| Editorial cleanup | `editorial/<scope>` | `editorial/glossary-pass` |

---

## PR review checklist (for reviewers)

Before approving a PR, confirm:

- [ ] PR template is fully filled in.
- [ ] Section reference is accurate.
- [ ] Change classification is correct (Correction / Addition / Deletion / Restructure).
- [ ] Rationale is specific and sourced.
- [ ] If a Mandatory standard changed, an ADR is linked or created.
- [ ] Markdown renders correctly (preview in the GitHub diff).
- [ ] No accidental changes to other sections.
- [ ] Cross-references in other sections are still valid.
- [ ] Glossary updated if new acronyms introduced.

---

## Architecture Decision Records (ADRs)

When a PR alters a contested standard, an ADR is required. ADRs live in `decisions/` and follow the template at [`decisions/ADR-template.md`](./decisions/ADR-template.md).

Each ADR captures:
- The decision
- The context (what was contested)
- The options considered
- The decision rationale
- Who approved

ADRs are **append-only**. If the WG later reverses a decision, a new ADR is written that supersedes the prior one — the prior one is never edited.

---

## Versioning

The Framework is versioned via Git tags:

- `v0.2` — first WG draft + Site Certification (current)
- `v0.3` — sub-group drafts integrated
- `v0.5` — first integrated cross-section pass
- `v0.9` — pre-final, post-external-consultation
- `v1.0` — WG-approved first draft to ACI Council

Each tag publishes a Release with PDF + DOCX + MD bundle attached.

---

## Questions?

- **Process question** → open a GitHub Issue with the `process` label.
- **Substantive question about content** → use the Google Doc comments or the Form.
- **Urgent** → contact the Chair directly.

---

_Last updated: with the v0.2 draft._
