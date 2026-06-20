# DS Dashboard Compatibility Checker

**PoV tool for checking if a Data Solutions dashboard can be transferred to a customer's instance.**

Analyzes every card's SQL queries to check:
- **Database access** — flags cards querying internal-only databases (DB 43/45)
- **Dataset packages** — identifies which packages the customer needs enabled
- **Table availability** — checks each table/schema against the customer's skill-context

Then lets you **transfer** compatible cards to a new folder in the customer's environment with one click.

## Quick Setup (30 seconds)
1. Download [`dashboard-compatibility-checker.html`](dashboard-compatibility-checker.html) from this repo
2. Open [Dialog](https://dialog.chainalysis.com) and start a new session
3. Drag the HTML file into the chat
4. Click the **expand/open button** on the rendered page to open in a standalone tab
5. Enter Dashboard ID + customer's DS API key + label → **Analyze**

## What You Need
| Input | Where to find it |
|-------|-----------------|
| **Dashboard ID** | From the URL: `data.chainalysis.com/visualizations/dashboard/`**3948**`-kyt-benchmarking` |
| **Customer's DS API Key** | `data.chainalysis.com` → customer's team → **Settings → API Keys** |
| **Customer label** | Just for display (e.g., "Citi", "CPS") |

## Alternative: Chat-Only
Ask Chain directly without the HTML page:

> *Run the ds-dashboard-compatibility-checker workflow for dashboard 2344 with customer API key ABC123 for CPS*

Text results in chat — no charts, but all the same data.

## What It Checks
| Layer | What it catches | Example |
|-------|----------------|---------|
| Database access | Cards querying internal-only DBs | KYT dashboards → `data_analyst_prod_catalog` |
| Internal schemas | SQL referencing admin-only schemas | `gold_compliance`, `due_diligence_silver_views` |
| Dataset packages | Tables missing from customer's access | `bitcoin.peer_cluster_pairs` (needs Geolocation) |

## Workflow
- **Slug**: `ds-dashboard-compatibility-checker`
- **Status**: Org-public, published v1, alias: `prod`
