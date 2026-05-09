# WG Feedback Form — Specification

This document is the spec for the Google Form that non-tech WG members use to submit feedback. Replicate this in Google Forms and link the responses to a Google Sheet.

---

## Form metadata

- **Title:** ACI Skydiving Framework — WG Feedback
- **Description (header text):**

> This form is for Working Group members who prefer not to use GitHub. Submit a separate form for each section or change you want to flag. Your submissions are reviewed daily by the WG Scribe and converted into Pull Requests on GitHub for the full WG to review. You will receive an email notification when your submission becomes a Pull Request.
>
> For comments and discussion (rather than proposed changes), use the Google Doc comment feature instead.

- **Settings:**
  - Collect email addresses: **Always**
  - Limit to one response: **No** (members will submit multiple)
  - Allow response editing: **Yes**
  - Show progress bar: **Yes**
  - Confirmation message: _"Thank you. Your submission has been logged. The Scribe will review within 2 working days. You'll receive an email when this becomes a Pull Request on GitHub, or if clarification is needed."_

---

## Questions

### Q1 — Your name

- Type: **Short answer**
- Required: **Yes**
- Validation: text length > 1

### Q2 — Your role on the WG

- Type: **Dropdown**
- Required: **Yes**
- Options:
  - Chair
  - Vice-Chair (Operations)
  - Vice-Chair (Safety)
  - Member — Regulatory
  - Member — Aircraft Operations
  - Member — Training
  - Member — Equipment
  - Member — Medical
  - Member — Insurance
  - Athlete Representative
  - Secretariat
  - External consultee (DGCA / AAI / IAF / insurer / other)

### Q3 — Section reference

- Type: **Short answer**
- Required: **Yes**
- Description: _"Examples: §2A.4.1, Part 3 §3.11, Part 4 (general). Be as specific as you can — it speeds up review."_

### Q4 — Type of feedback

- Type: **Multiple choice (single select)**
- Required: **Yes**
- Options:
  - Correction (factual error / typo)
  - Addition (new content needed)
  - Deletion (content should be removed)
  - Disagreement (I disagree with the current draft)
  - Question (I need clarification)
  - Other

### Q5 — Current text (if applicable)

- Type: **Paragraph**
- Required: **No**
- Description: _"Copy-paste the sentence or paragraph you're commenting on. Helps the Scribe locate your concern precisely."_

### Q6 — Your proposed change or question

- Type: **Paragraph**
- Required: **Yes**
- Description: _"What do you want changed, added, removed, or asked? Be as specific as you can. If you're proposing new text, write it out."_

### Q7 — Why? (rationale, source, concern)

- Type: **Paragraph**
- Required: **Yes**
- Description: _"Why does this matter? Cite a source if you have one (USPA SIM section, APF Reg, India regulation, your field experience). 'Because it's better' is not enough — give us the reasoning."_

### Q8 — Mandatory-standard impact (your view)

- Type: **Multiple choice (single select)**
- Required: **Yes**
- Options:
  - This does not change any Mandatory `[M]` standard
  - This changes a Mandatory standard
  - This adds a new Mandatory standard
  - I'm not sure — Scribe to assess

### Q9 — Anything else?

- Type: **Paragraph**
- Required: **No**

### Q10 — May we attribute this to you in the Pull Request?

- Type: **Multiple choice (single select)**
- Required: **Yes**
- Options:
  - Yes — attribute by name and role
  - Yes — attribute by role only
  - Please ask the Chair before attributing

---

## Sheet structure (auto-populated)

After Form responses link to a Sheet, add these **Scribe-managed** columns to the right of the Form-populated columns:

| Column | Owner | Values |
|---|---|---|
| Scribe Status | Scribe | New / Needs Clarification / Discussion Open / Ready / PR Raised / Merged / Rejected / Deferred |
| PR / Issue link | Scribe | URL |
| Notes | Scribe | Free text |
| Date Triaged | Scribe | Date |
| Date PR Raised | Scribe | Date |
| Date Closed | Scribe | Date |

Use Google Sheets' Conditional Formatting:
- Status = "New" → yellow background
- Status = "Needs Clarification" → orange
- Status = "PR Raised" → light blue
- Status = "Merged" → light green
- Status = "Rejected" / "Deferred" → grey

---

## Permissions

- **Form**: WG members have the link. Not publicly accessible.
- **Sheet**: Scribe has Editor; Chair has Editor; everyone else No Access (audit integrity).
- Submitters get an email confirmation but cannot view other submissions.
