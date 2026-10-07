# Lead Segmentation Dashboard

A browser-based tool that turns a raw list of retail leads into a scored, segmented outreach tracker.

**Live demo:** https://aaronchunie-lang.github.io/lead-dashboard/

## Why I built it

During my business development internship at NexSupply, I reached out to 50+ retailers and tracked them by hand in spreadsheets. Deciding who to contact first and who needed a follow-up took time and was inconsistent. This tool automates that work: upload a list, set your priorities, and see who to contact next.

## Features

- **CSV upload:** works with any lead list. Column names are matched flexibly (for example, `company`, `retailer` or `name`).
- **Adjustable scoring:** sliders set how much category fit, store count, region and engagement count toward a 0–100 score.
- **Automatic segments:** each lead is labeled High-fit, Warm or Cold, with thresholds you can change.
- **Follow-up flags:** leads contacted more than N days ago with no reply are flagged.
- **Dashboard:** key numbers, leads by segment, the outreach funnel, and reply rate by channel.
- **Status tracking:** change a lead's status in the table and the whole dashboard updates.
- **Export:** download the scored list as a CSV.

## How to use it

1. Open the page. Sample data loads automatically.
2. Click **Upload CSV** to use your own list. Recognized columns:

| Column | Example | Required |
|---|---|---|
| `name` | Maple Market | Yes |
| `category` | Streetwear | No |
| `region` | Midwest | No |
| `store_count` | 4 | No |
| `channel` | Instagram DM | No |
| `status` | Not contacted / Contacted / Replied / Meeting / Won / Lost | No |
| `last_contact` | 2026-09-15 | No |
| `email` | buyer@store.com | No |

3. Choose your target categories and regions, then adjust the sliders.
4. Filter to **Needs follow-up only** to see who to contact today.
5. Click **Export CSV** to save the results.

## How scoring works

Score = (weighted points earned ÷ total possible points) × 100

| Factor | Full points | Partial points |
|---|---|---|
| Category fit | Category is a selected target | 0 otherwise |
| Store count | 6+ stores | 2–5 stores: 60%; 1 store: 20% |
| Region fit | Region is a selected target | 30% otherwise |
| Engagement | Meeting or Won | Replied: 70%; Contacted: 35%; Not contacted or Lost: 0 |

To change these rules, edit the `sizePts`, `ENGAGE` and `score` functions in `index.html`.

## Tech

- A single `index.html` file in plain HTML, CSS and JavaScript, with no libraries and no build step
- Hosted on GitHub Pages
- Built with AI-assisted development (Claude)

## Data and privacy

Everything runs in the browser, and no lead data is uploaded anywhere. `sample_leads.csv` contains made-up companies only.
