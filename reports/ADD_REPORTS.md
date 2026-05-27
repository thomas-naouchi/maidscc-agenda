# Agent instructions — add new reports to the agenda

## Goal
Find HTML files in `reports/` that are not yet listed on the agenda, and add a card for each one.

## Step 1 — find missing reports

1. List every `.html` file in `reports/`.
2. Open `index.html` and read the `REPORTS_DATA` array (look for `const REPORTS_DATA = [` — everything up to the matching `];`).
3. Any filename from step 1 whose URL-encoded name does **not** appear in any `href` field is a missing report.

## Step 2 — extract metadata from each missing report

Open the report file and read:
- **title**: from the `<title>` tag or the first `<h1>` — strip the site name suffix (e.g. "· maids.cc") if present.
- **date**: look for a date in the `<h1>`, eyebrow/subtitle text, or anywhere in the first visible content. Format as `YYYY-MM-DD`. If only a month/year is found, use the last day of that month.
- **summary**: read the first narrative paragraph or KPI description and condense it to 1–2 sentences (max ~200 characters).
- **tags**: infer 1–3 short tags from the subject matter (e.g. `["Sales", "MMR"]`).
- **thumb**: `null` unless you find an image file in `reports/` that clearly matches this report.

## Step 3 — add entries to index.html

Insert one object per missing report into the `REPORTS_DATA` array in `index.html`. Place the newest report (by date) first.

```js
{
  title:   "...",
  date:    "YYYY-MM-DD",
  summary: "...",
  tags:    ["Tag1", "Tag2"],
  thumb:   null,
  href:    "reports/File%20Name.html",   // URL-encode spaces as %20
},
```

Only edit the `REPORTS_DATA` array. Do not touch anything else in `index.html`.
