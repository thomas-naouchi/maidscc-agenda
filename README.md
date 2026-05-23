# Agenda

Central landing page for my reports and studies.

## Setup

1. Open `index.html` and set your GitHub username + repo name at the top of the `<script>` block:
   ```js
   const GITHUB = {
     user:   "your-username",
     repo:   "your-repo-name",
     branch: "main",
     folder: "reports",
   };
   ```
2. Push this repo to GitHub.
3. In your repo → **Settings → Pages**, set the source to your `main` branch (root).
4. Your agenda is live at `https://<username>.github.io/<repo-name>`.

## Adding a report

1. Copy `reports/_template.html` to `reports/your-report-name.html`.
2. Edit the four `<meta>` tags at the top:
   ```html
   <meta name="report-title"   content="Report headline">
   <meta name="report-date"    content="2026-05-18">     <!-- YYYY-MM-DD -->
   <meta name="report-summary" content="One-line description.">
   <meta name="report-tags"    content="Ops, staffing">   <!-- comma-separated -->
   ```
3. Replace the body with your dashboard/charts.
4. Commit and push. The landing page picks it up automatically.

## Notes

- Files in `reports/` without a `report-title` meta tag are ignored — useful for drafts or shared assets.
- The landing page caches the file list for 5 minutes in the viewer's browser. Use the **refresh** button in the header to force a re-fetch.
- GitHub's API allows 60 unauthenticated requests/hour per IP; plenty for a manager + a few stakeholders.
