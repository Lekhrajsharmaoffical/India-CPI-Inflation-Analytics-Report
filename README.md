# India CPI Inflation Analytics Dashboard (2013–2023)

A fully formula-driven Excel model that analyzes a decade of India's Consumer Price Index (CPI) data across Rural, Urban, and All-India sectors — built so every number is traceable back to its source through live spreadsheet formulas, not hardcoded values.

---

## 📊 What This Project Is

This project takes India's official monthly CPI dataset (2013–2023, Base Year 2012=100) and turns it into an interactive, auditable Excel workbook. Instead of static charts and pasted numbers, every table, KPI, and chart in this workbook is powered by live formulas (`AVERAGEIFS`, `STDEV`, CAGR formulas, `RANK`, conditional logic) that pull directly from the raw dataset. Add a new month of data to the raw sheet, and every report sheet — tables, heatmaps, and charts — recalculates automatically.

**3,643 live formulas | 0 calculation errors | 8 interconnected sheets | 372 monthly records**

---

## 🗂️ Dataset Overview

| Detail | Description |
|---|---|
| **Source** | Government of India CPI data |
| **Time Period** | January 2013 – May 2023 |
| **Base Year** | 2012 = 100 (all values are indexed against 2012 prices) |
| **Sectors** | Rural, Urban, Rural+Urban (All-India composite) |
| **Categories Tracked** | 23 consumption categories (Cereals, Vegetables, Meat & Fish, Fuel & Light, Education, Health, etc.) plus 2 composite indices (Food & Beverages, General Index) |
| **Records** | 372 rows (one per Sector × Year × Month) |

### Data Cleaning Applied
- Fixed two data-entry typos in the `Month` column (a trailing-space `"November "` and a misspelled `"Marcrh"`)
- Added a `Month_Num` column (1–12) so months sort chronologically instead of alphabetically
- Confirmed that missing `Housing` values for the Rural sector are intentional (rural India is tracked as homeowners, not renters, so Housing CPI doesn't apply) — these are left blank rather than filled, to avoid distorting the data

---

## 🛠️ How This Report Was Built

The workbook is structured in two layers:

**1. Data Layer (`RawData` sheet)** — The cleaned dataset, untouched after cleaning. This is the only sheet you should ever add new data to.

**2. Calculation Layer (`CalcEngine` sheet)** — A dedicated formula engine that computes every intermediate metric used elsewhere in the report: yearly averages, year-over-year % change, volatility statistics (Std Dev, Coefficient of Variation), and CAGR (Compound Annual Growth Rate). Every other sheet references this layer or pulls directly from `RawData` — nothing is pasted in as a static number.

This two-layer design means the entire report is auditable: click any cell in any sheet, and the formula bar shows you exactly which raw data points and which formula produced that number.

---

## 📁 What's Inside Each Sheet

| Sheet | What It Contains |
|---|---|
| **RawData** | The full cleaned dataset (372 rows × 31 columns). Source of truth for all formulas. |
| **CalcEngine** | The formula engine — yearly averages, YoY% change, volatility (Std Dev / CV%), and CAGR calculations, all formula-driven and labeled by section. |
| **Overview** | Executive dashboard: KPI cards (decadal CPI rise, total inflation %), an annual trend line chart, and 12 detailed analytical insights covering COVID impact, rural-urban gaps, and category-level drivers. |
| **Rural_vs_Urban** | Side-by-side category comparison for 2023, a 10-year Rural vs Urban CPI trend chart, and absolute/percentage rise per category from 2013 to 2023. |
| **Volatility_Risk** | A volatility scorecard for every category and sector, using Coefficient of Variation (CV%) to flag which categories have the most unpredictable, swing-prone prices — with a HIGH / MEDIUM / LOW risk classification. |
| **YoY_Tracker** | Year-on-year % change for every category, every year, displayed as a color-coded heatmap (green = low inflation, red = high inflation) plus a General Index inflation trend chart. |
| **Rankings_CAGR** | Categories ranked by their 10-year Compound Annual Growth Rate (CAGR), showing which parts of the consumer basket inflated fastest. |
| **Food_Inflation** | A deep dive into food prices: a monthly Vegetables CPI matrix (to spot seasonal spikes), Rural vs Urban food category comparison, and trend lines for key food items. |

---

## 🔍 What You'll Learn From This Report

- **How much prices actually rose** — India's General CPI rose 61.4% over the decade (110.0 → 177.6), averaging roughly 4.9% annual inflation
- **Who was hit hardest** — Rural India faced higher CPI than Urban India in every single year from 2013 to 2023
- **Which categories are riskiest** — Meat & Fish recorded the fastest sustained price growth, while Vegetables and Oils & Fats showed the most extreme month-to-month volatility (the latter tied to global events like the Russia-Ukraine war)
- **Where policy worked** — Sugar prices stayed almost flat for a decade, a direct result of government price-control mechanisms
- **What COVID-19 did to prices** — 2020 produced a broad, simultaneous price shock across food, health, and household goods rather than a single-category spike

---

## ✏️ How to Update This Report With New Data

1. Open the **RawData** sheet
2. Add new rows below the existing data, following the exact same column structure (Sector, Year, Month, Month_Num, then each CPI category)
3. Make sure `Sector` is spelled exactly as `Rural`, `Urban`, or `Rural+Urban` (formulas match these text values exactly)
4. Save the file — all formulas in `CalcEngine` and every report sheet (Overview, Rural_vs_Urban, Volatility_Risk, YoY_Tracker, Rankings_CAGR, Food_Inflation) will recalculate automatically
5. If you're using Excel, this happens instantly. If you're using Google Sheets or another tool, you may need to trigger a manual recalculation (e.g., Ctrl + Alt + F9 in Excel, or re-open the file)

No formulas need to be rewritten or copied — the `AVERAGEIFS`-based design means new rows are picked up automatically as long as they fall within the referenced column ranges.

---

## 🎨 Formula Color Key (used throughout `CalcEngine`)

| Color | Meaning |
|---|---|
| 🔵 Blue text | Hardcoded input value (e.g., a Standard Deviation calculated once and stored as a reference point) |
| 🟢 Green text | A formula that pulls data from a different sheet |
| ⚫ Black text | A formula calculated within the same sheet |

---

## 🧰 Tools & Techniques Used

`AVERAGEIFS` · `STDEV` · `Coefficient of Variation (CV%)` · `CAGR formulas` · `RANK` · `IFERROR` · `Conditional Formatting (color scales)` · `PivotTable-style cross-tabulation` · `Line & Bar Charts` · Multi-sheet formula architecture
