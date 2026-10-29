# Weekly Funnel Report

Weekly outreach funnel, grouped by the week of Date Added.
Currently runs on **fake data**; the real Google Sheet sync replaces `seed_fake_data.py` later.

## What runs

`.github/workflows/report.yml` runs daily, on push to `main`, and on demand:

1. `python seed_fake_data.py` builds `funnel.db` (SQLite) from `schema.sql`
2. `python report.py` reads the views and writes `site/index.html`
3. The `site/` folder is deployed to GitHub Pages

## Run locally

    python3 seed_fake_data.py && python3 report.py
    python3 -m http.server 8765 --directory site

Then open http://localhost:8765

## Files

| File | Purpose |
|---|---|
| `schema.sql` | tables, `status_map`, funnel and status-change views |
| `common.py` | today's date, week start day (Sunday), status to stage map |
| `seed_fake_data.py` | fake leads and daily snapshots for 4 tabs |
| `report.py` + `template.html` | builds the single-file report |
