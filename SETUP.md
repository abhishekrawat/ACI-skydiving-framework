# Setup Guide — One-time configuration

This guide is for **Abhishek** (the Maintainer) to complete after pushing this repo to GitHub. It covers the configuration that can't be committed to the repo (it's all done in GitHub web UI and in Google Cloud).

Estimated time: **30–45 minutes** end to end.

---

## Step 1 — Create the GitHub repository

1. Go to https://github.com/new
2. Owner: `abhishekrawat`
3. Repository name: `ACI-skydiving-framework`
4. Description: `Working Group drafting workspace for the India National Framework for Civilian Skydiving Dropzone Operations`
5. **Visibility: Private**
6. **Do NOT** check "Add a README", "Add .gitignore", or "Add a license" — this repo brings its own.
7. Create repository.

---

## Step 2 — Push this scaffold

In your terminal:

```bash
cd /path/to/ACI-skydiving-framework
git init
git add .
git commit -m "Initial scaffold: framework v0.2 + WG operating documents"
git branch -M main
git remote add origin git@github.com:abhishekrawat/ACI-skydiving-framework.git
git push -u origin main
```

(If you're using HTTPS rather than SSH: `https://github.com/abhishekrawat/ACI-skydiving-framework.git`.)

---

## Step 3 — Configure branch protection on `main`

This is the single most important step. It is what makes you the merge gatekeeper.

1. In the GitHub repo, go to **Settings → Branches**.
2. Click **Add branch ruleset** (or the older **Add rule**).
3. Branch name pattern: `main`
4. Configure:
   - ✅ **Require a pull request before merging**
   - ✅ **Require approvals** — set to **2**
   - ✅ **Dismiss stale pull request approvals when new commits are pushed**
   - ✅ **Require review from Code Owners**
   - ✅ **Require conversation resolution before merging**
   - ✅ **Require status checks to pass before merging** — add `validate-pr` (the workflow from `.github/workflows/pr-validation.yml`; it'll appear in the dropdown after the workflow has run at least once)
   - ✅ **Require linear history** (enforces squash-and-merge style)
   - ✅ **Restrict who can push to matching branches** — add only your username
   - ✅ **Do not allow force pushes**
   - ✅ **Do not allow deletions**
5. Save.

> **Test it works:** Try to push directly to `main`. GitHub should reject it.

---

## Step 4 — Add WG members as Collaborators

1. **Settings → Collaborators → Add people**
2. Add the GitHub usernames of every tech-comfortable WG member.
3. Set role: **Write** (they can push branches and open PRs but cannot merge to `main`).
4. Set your own role to: **Admin** (you, the Chair).
5. Email invites will be sent.

For non-tech WG members: they don't need GitHub accounts. Skip them.

---

## Step 5 — Set up the Google Doc mirror (optional but recommended)

This makes the Pandoc → Google Drive sync actually work. If you want to do this later, you can — the `pr-validation` workflow runs without it.

### 5a — Create a Google service account

1. Go to https://console.cloud.google.com/
2. Create a new project (or use an existing one). Name suggestion: `aci-wg-skydiving`.
3. Enable the **Google Drive API** for this project: **APIs & Services → Library → Google Drive API → Enable**.
4. Create a service account: **IAM & Admin → Service Accounts → Create Service Account**.
   - Name: `aci-skydiving-publisher`
   - Skip the "Grant access" steps (we'll do that on the Drive folder).
5. Open the service account → **Keys → Add Key → JSON**. A JSON file downloads. **Keep this safe.**

### 5b — Create a Google Drive folder and share with the service account

1. In Google Drive, create a folder. Suggestion: `ACI Skydiving WG — Latest Drafts`.
2. Right-click → **Share** → add the service account's email (looks like `aci-skydiving-publisher@aci-wg-skydiving.iam.gserviceaccount.com`).
3. Give it **Editor** access.
4. Copy the folder ID from the URL: `https://drive.google.com/drive/folders/<THIS_IS_THE_ID>`.
5. Share the folder with WG members as **Viewers** (read-only).

### 5c — Add secrets to GitHub

1. In the GitHub repo: **Settings → Secrets and variables → Actions → New repository secret**.
2. Add two secrets:
   - `GDRIVE_SERVICE_ACCOUNT_JSON` — paste the entire JSON file content from step 5a.
   - `GDRIVE_FOLDER_ID` — paste the folder ID from step 5b.
3. Save.

### 5d — Test it

1. Make a trivial edit to `framework/india_skydiving_framework.md` (add a space, save).
2. Open a PR, approve, merge.
3. Watch **Actions** tab — the `Sync framework to Google Drive` workflow should run.
4. Check the Drive folder — `ACI_Skydiving_Framework_latest.docx` should appear.

---

## Step 6 — Create the WG Feedback Form

A separate Google Form for non-tech members. Drafted in `annexes/wg-feedback-form-spec.md`.

1. Go to https://forms.google.com/
2. Create a new form titled **"ACI Skydiving Framework — WG Feedback"**.
3. Add the questions per `annexes/wg-feedback-form-spec.md`.
4. Set responses to populate a Google Sheet (Form → Responses → Link to Sheets).
5. Share the Form link with non-tech WG members.
6. Update `README.md` and `CONTRIBUTING.md` to add the actual links.

---

## Step 7 — Designate the Scribe

1. Decide who the Scribe is.
2. Grant them:
   - **Edit** access to the Form-responses Sheet.
   - **Write** access to the GitHub repo.
3. Have them read `SCRIBE_PROCESS.md`.
4. Designate a backup Scribe with the same access.

---

## Step 8 — Tag v0.2

After all of the above is working:

```bash
git tag -a v0.2 -m "First WG draft + Site Certification (Part 2A)"
git push origin v0.2
```

This creates the first formal version anchor.

---

## Step 9 — Onboard the WG

Send the WG:

1. **For tech members**: link to `CONTRIBUTING.md`. Walk them through one PR.
2. **For non-tech members**: link to the Google Doc + Feedback Form + the non-tech onboarding doc (in `annexes/`).
3. Hold a 30-min Zoom walkthrough — record it for absentees.

---

## Troubleshooting

**"My PR was merged but the Google Doc didn't update."**
Check **Actions** tab for the workflow run. If it failed, the most common causes:
- Service account JSON malformed in the secret.
- Service account doesn't have Editor access to the folder.
- Pandoc choking on a malformed Markdown table — check the workflow log.

**"I can't push to `main`."**
That's the point. Open a PR.

**"The PR validation check is failing."**
Read the failure output. Most common cause: PR template not filled in. Edit the PR description and re-run the check (Actions → re-run failed jobs).

---

## Roll-back / disaster recovery

- All commits are in Git. Rollback is `git revert <commit>`.
- All Form submissions are in the Google Sheet — even those not yet converted to PRs.
- All ADRs are append-only and preserved.
- The `v0.2` tag preserves the current state forever.
- The DOCX/PDF artifacts are also stored in GitHub Actions artifacts for 90 days.

If the GitHub repo is ever lost: clone it locally now and keep that clone. (One simple command: `git clone https://github.com/abhishekrawat/ACI-skydiving-framework.git ~/backup-aci-wg`. Run weekly.)
