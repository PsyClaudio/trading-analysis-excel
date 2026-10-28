# Trading Operations Analysis with Excel

Excel analysis of trading operations, developed by **Claudio Lombardi** for the Advanced Data Analysis with Excel course in the ProfessionAI Master in Data Analytics.

## Project overview

The FinTrack Solutions educational case study follows a trader's stock transactions across international exchanges. The workbook combines transaction records, a PivotTable, holding-period and profit calculations, a histogram, and a contingency table with empirical probabilities.

## Workbook structure

| Worksheet | Content |
| --- | --- |
| My Trades | 200 transaction records with exchange, region, purchase and sale dates, quantity and prices |
| Stock Exchanges | PivotTable summarizing share quantities by region and exchange, with a threshold-based Yes/No classification |
| Profit Insights | Holding period in days, profit or loss for each transaction, and a holding-period histogram with commentary |
| Number of Trades Exchanged | Counts by region and share quantity, marginal totals, and two probability calculations |

## Verified dataset summary

- **200** transactions with unique identifiers.
- **21** stock exchanges and **17** region labels.
- **1,019** total shares across the transactions.
- Purchase dates: **2 January 2021–30 December 2022**.
- Sale dates: **2 January–15 June 2023**.

The `Region` field follows the supplied dataset and includes country, territory and broader regional labels. Transaction identifiers are eight-character strings.

## Methods

### Holding period and profit

Holding period is calculated as sale date minus purchase date. Profit is calculated as:

```text
Profit = (Sell Price − Buy Price) × Quantity
```

The workbook displays transaction profit in US dollars with five decimal places, as required by the assignment. The calculation uses only the supplied prices and quantities; it does not incorporate transaction costs or currency conversion.

The histogram summarizes holding periods. Its accompanying discussion is a visual assessment of the distribution, not a formal test of normality.

### PivotTable and conditional logic

The PivotTable aggregates **Quantity**, representing shares rather than the number of transaction records. An `IF` formula classifies region totals using a threshold of **67 shares**, with totals greater than or equal to 67 flagged Yes.

The tax-related flag implements the exercise's hypothetical rule. It does not calculate an actual tax liability.

### Contingency table and probabilities

`COUNTIFS` builds frequencies by region and share quantity. Marginal totals reconcile to 200 transactions. `INDEX` and `MATCH` retrieve the United Kingdom count; the Asian-region calculation combines the selected region rows.

| Joint event | Matching transactions | Empirical probability |
| --- | ---: | ---: |
| United Kingdom and quantity equal to 1 | 1 / 200 | 0.50% |
| Asian region and quantity at most 8 | 74 / 200 | 37.00% |

Asian-region labels included in the calculation are China, Hong Kong, India, Iran, Japan, Saudi Arabia, South Korea and Taiwan. Both probabilities use **all 200 transactions** as their denominator; they are joint frequencies, not probabilities conditional on being in the selected region.

## Validation

The saved holding-period and profit results were checked against all 200 source records. All 170 interior contingency-table counts were independently recomputed and matched the saved results. The two event counts and the total share quantity were also reconciled with the source transactions.

## How to use

Download `trades_on_exchanges - Portfolio.xlsx` and open it in a current desktop version of Microsoft Excel. Review the four worksheets in order. The workbook includes a Data Model-backed PivotTable and an Excel histogram, so other spreadsheet applications may not reproduce every native feature.

The analysis is built around the supplied 200-row dataset. To extend it, update the source ranges, profit and duration formulas, contingency-table ranges and chart source, then refresh the PivotTable and verify totals. The workbook should not be assumed to expand every analytical range automatically.

## Skills demonstrated

Microsoft Excel · PivotTables · Conditional formulas · COUNTIFS · INDEX/MATCH · Date calculations · Histograms · Contingency tables · Empirical probability · Data validation and reconciliation

## Author

**Claudio Lombardi** — [GitHub portfolio](https://github.com/PsyClaudio)

