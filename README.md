# Google Fiber Data Pipeline Project

A end-to-end data pipeline project built to help the Google Fiber customer 
service team understand repeat caller trends and measure how effectively 
the team resolves customer issues on the first contact.

## Project Overview

The Google Fiber customer service team needed insights into how often 
customers call back after their first inquiry. This project ingested three 
separate market datasets into BigQuery, merged them into a single reporting 
table using SQL, and built an interactive Tableau dashboard to visualize 
repeat caller trends across markets and issue types.

## Tools Used
- **BigQuery** — data storage and SQL merging
- **Tableau Public** — interactive dashboard and visualizations
- **GitHub** — version control and portfolio documentation

## Data Pipeline

### Source Data
Three separate tables in BigQuery, one per market:

| Table | Description |
|-------|-------------|
| Market1 | Customer contact data for Market 1 |
| Market2 | Customer contact data for Market 2 |
| Market3 | Customer contact data for Market 3 |

### What Each Table Contains

| Column | Description |
|--------|-------------|
| `date_created` | Date of first customer contact |
| `contacts_n` | Number of first contacts |
| `contacts_n_1` | Repeat contacts on day 1 after first call |
| `contacts_n_2` | Repeat contacts on day 2 after first call |
| `contacts_n_3` | Repeat contacts on day 3 after first call |
| `contacts_n_4` | Repeat contacts on day 4 after first call |
| `contacts_n_5` | Repeat contacts on day 5 after first call |
| `contacts_n_6` | Repeat contacts on day 6 after first call |
| `contacts_n_7` | Repeat contacts on day 7 after first call |
| `new_type` | Issue type (type_1 through type_5) |
| `new_market` | Market identifier (market_1, market_2, market_3) |

### Merging in BigQuery
The three market tables were merged into a single reporting table 
using UNION ALL in BigQuery. See `data_merging.sql` for the full query.

### Final Output
- 1,350 rows
- 11 columns
- Q1 2022 data (January – March)
- 3 markets, 5 issue types
- Exported as CSV and connected to Tableau

## Dashboard Features
The Tableau dashboard answers four key stakeholder questions:

- **Repeat call frequency** — how often do customers call back after first contact?
- **Issue types** — which problem types generate the most repeat calls?
- **Market trends** — how do repeat calls differ across the 3 markets?
- **Time flexibility** — trends viewable by week, month, quarter, and year

### Charts included
- 4 KPI summary cards (First Contacts, Repeat Contacts, Repeat Rate, Top Issue Type)
- Repeat calls over time (line chart, filterable by time period)
- Repeat calls by market (bar chart)
- First-call resolution rate by market (bar chart)
- Repeat calls by issue type (bar chart)
- Day-of-repeat breakdown — N+1 through N+7 (bar chart)

## Key Findings
- **Market 1** had the highest repeat call volume
- **Type 5** issues generated the most repeat contacts
- Most repeat calls happen within the first 2 days after the initial contact
- Overall repeat rate was approximately **27.98%**

## Files
- `data_merging.sql` — BigQuery SQL query used to merge the three market tables
- `bigquery_merge.png` — screenshot of the BigQuery query
- `google_fiber_dashboard.twbx` — Tableau workbook
- `data/merged_data.csv` — final merged dataset used in Tableau

## Live Dashboard
https://public.tableau.com/app/profile/terence.ting.yong.rui/viz/GoogleFibreProject_17788982424210/DashboardGoogleFibre
