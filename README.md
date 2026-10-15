# PaySim Fraud Analytics | Interactive Excel Dashboard

**Excel portfolio project | PivotTables · Slicers · SUMIF · SUMPRODUCT · Data Quality Checks**

Interactive spreadsheet analysis of **10,000 synthetic PaySim transactions**, exploring how labelled fraud varies by transaction amount, payment type and simulation step. The workbook combines three native PivotTables, connected slicers, charts, reporting formulas and reconciliation checks.

> **Scope:** Exploratory analysis of synthetic records—not live banking data, a production fraud detection system or a predictive model. PaySim amounts are synthetic monetary units, not verified EUR amounts or realised financial losses.

## Business question

**How are labelled fraud cases distributed across transaction amounts, payment types and simulation steps, and how can an analyst explore those patterns interactively?**

## At a glance — full sample

| Metric | Value |
| --- | ---: |
| Transactions | 10,000 |
| Labelled fraud cases | 68 |
| Fraud rate | 0.68% |
| Total transaction amount | 1,035,466,899.49 synthetic units |
| Most labelled fraud cases by amount | 10k–100k: 42 / 68 (61.8%) |
| Highest observed amount-band fraud rate | 1m+: 8 / 123 (6.50%) |
| Payment types containing labelled fraud | TRANSFER (33) and CASH_OUT (35) |

**Interpretation:** The 1m+ band contains only 123 transactions, so its high rate should not be generalised. Rates can be unstable for small filtered groups.

## Workbook

| Sheet | Purpose |
| --- | --- |
| START HERE | Context, baseline KPIs, findings and limitations |
| PIVOT - AMOUNTS | Fraud reporting by amount band |
| PIVOT - TYPES | Fraud reporting by payment type and three slicers |
| PIVOT - STEPS | Fraud reporting by simulation step |
| QUALITY CHECKS | Source-level checks and PivotTable reconciliation |
| SOURCE TRANSACTIONS | Transaction-level reporting rows and derived columns |
| DASHBOARD | Interactive KPIs, charts and data tables |

### Interactive dashboard

The **Type**, **Amount Band** and **Step** slicers connect to the three PivotTables. Dashboard tables use category-aware formulas so that filtered PivotTable rows do not have to remain in fixed positions.

The dashboard contains filtered **Transactions**, **Fraud Cases** and **Fraud Rate** KPIs, plus charts for fraud rate by amount band, fraud cases by payment type and fraud rate by simulation step. The **Total Amount — Full Sample** KPI deliberately remains unfiltered. Business takeaways are explicitly labelled as findings from the full sample.

### Excel techniques

- Native PivotTables with shared slicer/report connections
- Derived columns: Amount Band, Transactions, Fraud Cases and Fraud Amount
- `SUMIF` and `SUMPRODUCT` for category-aware chart data
- `INDEX` / `MATCH` to find PivotTable Grand Totals after filtering
- `IFERROR`, percentages, conditional formatting and reconciliation checks

**Quality-check distinction:** agreement across the three filtered PivotTables is not an independent verification of each filtered transaction against the raw data.

## Findings — full 10,000-row sample

1. **Amount:** The 10k–100k amount band contains **42 of the 68 fraud labels (61.8%)**; 42 out of 2,841 transactions in that band are labelled fraud (**1.48%**).
2. **Type:** TRANSFER has **33 fraud cases out of 921 (3.58%)** and CASH_OUT has **35 out of 1,321 (2.65%)**. No other payment type has labelled fraud cases in this sample.
3. **Simulation step:** This extract covers PaySim steps 1–7. These step-level comparisons do not establish real-world seasonality or causal trends.

## How to use

1. Download [`PaySim_Fraud_Analytics_Working.xlsx`](./PaySim_Fraud_Analytics_Working.xlsx).
2. Open the workbook in a compatible desktop spreadsheet application. The interactive slicers were exercised in **WPS Office for Windows**.
3. In `PIVOT - TYPES`, change the **Type**, **Step** and **Amount Band** slicers.
4. Open `DASHBOARD` to inspect the filtered KPIs and charts.
5. Review `QUALITY CHECKS`, then clear all slicers to return to the full sample.

### Validation scope

Manual checks in WPS Office covered the baseline view, 10k–100k band, TRANSFER-only and Step 4 filters, matched PivotTable totals, reopening the saved workbook, and a single-PivotTable refresh.

**Not fully tested:** changing the raw source followed by a complete Refresh All, all possible slicer combinations, and full cross-version Microsoft Excel compatibility. **Power Query was not used.**

## Data provenance and limitations

- The workbook uses the **first 10,000 rows** of the [published PaySim deployment sample CSV](https://raw.githubusercontent.com/alice-patrick/decision-centric-fraud-framework/refs/heads/main/data/deployment/paysim_deployment_sample.csv), not the entire PaySim dataset.
- Synthetic fraud labels and amounts are not evidence of actual financial loss or real-world fraud prevalence.
- Account identifiers and balance fields were excluded from this reporting workbook; account-level checks are outside its scope.
- Dashboard insights are descriptive, not predictive.

## Related work

This Excel-focused portfolio project complements the [Fraud Decision Analytics repository](https://github.com/alice-patrick/fraud-decision-analytics) and the broader decision-centric MSc project. Its purpose is to demonstrate practical **Excel reporting, exploratory analysis, interactive filtering and data-quality reasoning**.
