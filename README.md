# Amazon_PPC_pipeline
Automated Amazon PPC analysis pipeline (Python + pandas → Excel exec summary) with campaign/ASIN targeting insights and growth playbook.

The pipeline ingests Amazon **Advertised Product** and **Targeting** reports, cleans and standardizes the data, computes key PPC metrics (CTR, CVR, CPC, ACOS, ROAS), and aggregates performance at the campaign, ASIN, portfolio, targeting-type, and day-of-week levels. It then exports a multi-sheet Excel file with ready-to-use tables for an executive summary.

## Features

- **Data ingestion**
  - Reads raw Amazon PPC exports (Advertised Product report + Targeting report) from CSV.
- **Cleaning & enrichment**
  - Normalizes date and currency fields.
  - Derives metrics: CTR, CVR, CPC, ACOS, ROAS, day_of_week, target_type (Keyword/ASIN/Category), campaign_type (Auto/Manual).
- **Aggregated “pivot” tables**
  - Campaign-level performance (spend, sales, ACOS/ROAS, CTR, CVR).
  - ASIN-level and portfolio-level performance (hero vs laggard products).
  - Targeting efficiency by type: Keyword vs ASIN vs Category, Auto vs Manual.
  - Day-of-week performance summary.
- **Exec-focused slices**
  - Top “Winners” and “Bleeders” (campaigns/ASINs) by sales/ACOS.
  - Targeting Efficiency by Type table.
  - Negative keyword/ASIN candidate list (high clicks/spend, zero/poor sales).
- **Excel executive workbook output**
  - Uses `xlsxwriter` to generate a multi-sheet Excel file:
    - `Analysis_Advertised` / `Analysis_Targeting` (detailed summaries)
    - `EXEC_DATA` with labeled sections:
      - *Winners (Campaigns / ASINs)*
      - *Bleeders (Campaigns / ASINs)*
      - *Targeting Efficiency by Type*
      - *Negative Keyword / ASIN Candidates*
  - Designed to support a one-page “Growth Marketing Analysis: Scale & Systems Strategy” sheet with minimal manual formatting and narrative text.

## Tech stack

- Python 3
- pandas, NumPy
- XlsxWriter (via `pd.ExcelWriter`)
- (Optional) Google Colab / Jupyter for development

## Project structure (example)

```text
.
├── data/
│   ├── sample_advertised.csv      # anonymized sample input (Advertised Product report)
│   ├── sample_targeting.csv       # anonymized sample input (Targeting report)
├── notebooks/
│   └── amazon_ppc_analysis.ipynb  # exploration & development
├── src/
│   └── ppc_pipeline.py            # main pipeline script
├── outputs/
│   └── Amazon_PPC_Exec_Summary_example.xlsx  # example generated workbook
├── README.md
└── requirements.txt
