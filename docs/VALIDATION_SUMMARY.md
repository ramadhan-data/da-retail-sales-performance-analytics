# Validation summary

## Headline numbers (workbook value = independent pandas value computed from the raw CSV, difference 0)
| Item | Value |
|---|---|
| Source rows / columns | 495,478 / 9 (Raw_Data = Cleaned_Data row count) |
| Rows included in sales metrics | 491,318 |
| Rows excluded (kept in Cleaned_Data) | 4,160: 2,476 price <= 0, 1,681 non-product, 3 adjustment invoice |
| Gross sales / returns / net sales | 16,996,677.58 / -866,073.05 / 16,130,604.53 |
| Net units | 4,396,211 |
| Unique sale invoices / identified customers | 17,901 / 3,916 |
| Average order value (mean / median) | 949.48 / 583.56 |
| Rows flagged for review | 4,392 |
| Sum Quantity x UnitPrice (raw) vs sum Line_Amount (cleaned) | 15,910,296.13 both |

## Checks performed
1. LibreOffice recalculation of a random sample copy (900 invoices, 19,753 rows, identical formulas): 119,363 formulas, 0 errors.
2. 839 summary-sheet formula cells compared with pandas values: 0 mismatches.
3. 6 row-level formula columns in Cleaned_Data compared on all 19,753 sample rows: 0 mismatches.
4. Dashboard filters: 4 Month/Category combinations x 7 KPIs compared with pandas (28 comparisons): all matched, covering all four customer-count branches.
5. In the final workbook, `Analysis` section 7 holds 18 reconciliation checks and 3 error scans; cached result is "ALL OK".
6. Dashboard image rendered by LibreOffice from a values-only copy of the dashboard (not a screenshot from Excel).

## Not tested / limits
- The full 495,478-row file was not recalculated by a spreadsheet engine: LibreOffice was killed for memory (exit 137). Its stored values come from pandas using the same logic that was verified on the sample.
- Not opened in desktop Microsoft Excel (load time, rendering, dropdown behaviour untested).
- No native PivotTables; no Excel Tables.
- Customer decile table, first-occurrence flags and duplicate flag are static values (cross-checked, not formula-driven).
- Profit and regional analysis are impossible with this file (no cost column; single Region/Country value).
