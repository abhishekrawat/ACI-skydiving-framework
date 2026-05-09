# Scribe Process

This document is the operational manual for the **Scribe** role on the ACI Skydiving Framework Working Group. The Scribe converts feedback from non-tech WG members (submitted via Google Form) into Pull Requests on this repository.

The Scribe role is an **administrative role**, not a content authority. The Scribe does not unilaterally decide what changes; the Scribe converts proposed changes into the format the WG can review and approve.

---

## Who is the Scribe?

A designated WG member — typically the Secretariat or a delegate appointed by the Chair. Currently: _[to be assigned]_.

A backup Scribe should also be designated to cover absences.

---

## What the Scribe does (and does not) do

| The Scribe DOES | The Scribe does NOT |
|---|---|
| Triage Form submissions daily | Decide whether a change is a good idea |
| Convert clear submissions into PRs | Edit Mandatory standards on their own initiative |
| Attribute submissions to the original author | Anonymise feedback unless explicitly asked |
| Ask the submitter for clarification when needed | Reject submissions outright |
| Link related Form submissions together | Merge their own PRs |
| Tag the right WG members for review | Approve PRs as the second reviewer (conflict of interest) |

---

## Daily rhythm

| Frequency | Task |
|---|---|
| Daily (or every 2 days) | Triage new Form submissions in the Sheet |
| As needed | Reply to submitters needing clarification |
| Weekly | Review backlog of submissions not yet converted to PRs |
| Weekly | Provide the Chair with a digest of pending Form items |

---

## Tools

- **Google Form**: collects feedback. _[link to be added]_
- **Google Sheet**: receives Form responses (auto-populated). _[link to be added]_
- **GitHub repository**: where PRs are raised. https://github.com/abhishekrawat/ACI-skydiving-framework
- **Slack/Email channel**: backchannel to ask submitters for clarification.

---

## Sheet column structure

The Sheet has these columns (auto-populated from the Form, plus Scribe-managed columns):

| Column | Source | Purpose |
|---|---|---|
| Timestamp | Form | Submission time |
| Email | Form | Submitter's email |
| Name | Form | Submitter's name |
| Role | Form | Submitter's WG role |
| Section | Form | Section reference (e.g., §2A.4.1) |
| Change type | Form | Correction / Addition / Deletion / Question / Disagreement |
| Current text | Form | Quoted current text |
| Proposed change | Form | Proposed new text or change |
| Rationale | Form | Why |
| **Scribe status** | Scribe | Triage state: New / Needs Clarification / Ready / PR Raised / Merged / Rejected / Deferred |
| **PR link** | Scribe | URL of the resulting PR |
| **Notes** | Scribe | Any context |

---

## The triage decision tree

When a new Form submission arrives, the Scribe walks this tree:

```
New submission
     │
     ▼
Is the section reference clear and the proposed change actionable?
     │
     ├── No  ──► Mark "Needs Clarification"; reply to submitter via email.
     │            Wait up to 5 working days. Escalate to Chair if no response.
     │
     └── Yes ──► Is this a Question (not a change request)?
                  │
                  ├── Yes ──► Open a GitHub Issue (not a PR), tag relevant WG members,
                  │            link the Sheet row, mark Sheet as "PR Raised" with Issue URL.
                  │
                  └── No  ──► Does this change a Mandatory [M] standard?
                              │
                              ├── Yes ──► Open a GitHub Issue first ([Discussion] template);
                              │            await WG direction before opening PR.
                              │            Mark Sheet as "Discussion Open".
                              │
                              └── No  ──► Open a PR following the steps below.
                                           Mark Sheet as "PR Raised" with PR URL.
```

---

## Step-by-step: opening a PR from a Form submission

### Step 1 — Validate the submission

- Read the submission end-to-end.
- Confirm the section reference exists in the current draft.
- Confirm the "current text" actually matches the current draft. If not, the submitter may be looking at an old version — clarify.
- Confirm the proposed change is unambiguous.

### Step 2 — Create a branch

Branch naming convention: `scribe/<member-shortname>-<section>`.

Examples:
- `scribe/medical-2a7` — submission from Member-Medical on §2A.7
- `scribe/insurance-66` — submission from Member-Insurance on §6.6

If the submitter has multiple submissions for the same section, append a sequence: `scribe/medical-2a7-2`.

### Step 3 — Make the edit

- Edit only the section the submission is about.
- Match the existing Markdown style precisely (table formatting, list markers, heading levels).
- Do not "improve" the proposed text beyond what the submitter said. If the proposed text needs editing for fit, leave a comment in the PR explaining what you changed and why.

### Step 4 — Commit message

Format:
```
§<section>: <short description>

Originated from Form submission by <Name> (<Role>) on <date>.
Sheet row: <row number or link>.
```

Example:
```
§2A.7: add HEMS retainer as Aspirational at all tiers

Originated from Form submission by Dr. Asha Mehta (Member-Medical)
on 2026-05-12. Sheet row 47.
```

### Step 5 — Open the PR

Fill in the PR template:
- **Summary**: clear one-liner.
- **Section reference**: from the submission.
- **Change classification**: from the submission.
- **Mandatory-standard impact**: from your triage assessment. If "changes a Mandatory standard", an ADR must be linked — but you should have routed this through Discussion first.
- **Rationale**: quote the submitter's rationale verbatim. Add nothing of your own opinion.
- **Originating source**: tick "Scribe-raised on behalf of" and fill in name, role, and Sheet row.

### Step 6 — Tag reviewers

- Chair (Abhishek) is auto-assigned via CODEOWNERS.
- Add at least one other reviewer relevant to the section's domain (e.g., for §2A.7 medical changes, add Member-Medical even if they originated it — they should approve their own intent was captured correctly).

### Step 7 — Notify the submitter

Reply to the original Form submission email with the PR link.

### Step 8 — Update the Sheet

- Status → "PR Raised"
- PR link → URL
- Notes → any clarifications

---

## Handling clarifications

If the submission is unclear:

1. Reply to the submitter via email (do not call them — written record matters).
2. State exactly what's unclear.
3. Wait up to 5 working days.
4. If no response, escalate to Chair with the Sheet row.
5. After Chair direction, either close the submission as "Cannot Process" or proceed.

Never open a PR with a guess about the submitter's intent.

---

## Handling rejections

The Scribe never rejects a submission unilaterally. If a submission is technically infeasible (e.g., section doesn't exist, change contradicts a recently-merged PR), reply to the submitter explaining the issue and ask whether they want to revise. If the WG ultimately decides not to incorporate, the rejection comes through the PR review process, not the Scribe.

---

## Confidentiality

- Form submissions are WG-internal.
- Submitters' names appear in PR descriptions (this is the audit trail).
- If a submitter asks for anonymity, refer to the Chair — anonymous submissions degrade the audit trail and should be exceptional.

---

## Backup & continuity

- The backup Scribe should be granted equivalent access to the Sheet and the GitHub repo.
- During the primary Scribe's planned absences, the Sheet's "assignee" should be temporarily switched.
- If the primary Scribe is unexpectedly unavailable for >2 working days, the Chair re-assigns active submissions.

---

## Metrics the Scribe should track (weekly)

- Submissions received this week
- Submissions converted to PRs
- Submissions awaiting clarification
- Median time from Form submission to PR raised
- Backlog count

These go into the weekly digest the Chair shares with the WG.

---

_Last updated: with v0.2 of the Framework._
