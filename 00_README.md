# Analysis of Childhood Immunisation Coverage Using Excel

A fictional NGO collected immunisation data from **500 children** across **3 counties, 6 districts and 12 health facilities**. This project simulates the dataset, cleans it, analyses it in Excel and communicates the findings to programme managers.

> **All data are simulated** for a training exercise. Facility and place names are illustrative.

## Files

| File | What it is |
|---|---|
| `01_Original_Simulated_Dataset.csv / .xlsx` | Raw data as "collected": 508 rows (500 children + 8 duplicate entries) with deliberate quality problems |
| `02_Cleaned_Dataset.csv / .xlsx` | Clean data: 500 unique children, 17 columns (15 collected + 2 derived) |
| `03_Immunisation_Analysis_Workbook.xlsx` | Main workbook: **Dashboard**, **Analysis** (summary tables), Dashboard_Data, Clean_Data, Raw_Data, Data_Dictionary, Cleaning_Log, README |
| `04_Analytical_Report.docx / .pdf` | 3-page analytical report |
| `05_Summary_Tables.xlsx` | Standalone summary tables (values) for overall, district, facility and subgroup results |
| `06_Data_Dictionary_and_Cleaning_Documentation.docx` | Cleaning workflow, problem-by-problem log, missing-value table, validation checks, data dictionary |
| `07_Data_Dictionary.csv` | Data dictionary in CSV form |
| `08_Key_Findings_Presentation.pptx` | 8-slide summary of the findings |

## Dataset variables
Child ID, age in months, sex, county, district, health facility, mother's education, residence, BCG, OPV, Penta 1, Penta 3, measles, card availability, missed vaccination. Derived: `Age_Group`, `Penta_Dropout`. See the data dictionary.

## Data cleaning (summary)
Duplicates (8), inconsistent categories (Y/yes/1, M/male, abbreviated facility names), text in the age field, impossible ages (5), county-district mismatches (7), Penta 3 given without Penta 1 (9), missing values and a contradictory `Missed_Vaccination` field. Each is logged with the number of records affected and the correction. Full detail is in the `Cleaning_Log` sheet and document 06.

## Definitions
- **Coverage** = Yes / (Yes + No) for each vaccine. "Unknown" is excluded from the denominator.
- **Dropout** = (Penta 1 coverage − Penta 3 coverage) / Penta 1 coverage. WHO benchmark: above 10% is a concern.
- **Fully immunised** = all five vaccines "Yes", as a share of all 500 children.
- Targets (90% coverage, 10% dropout) are editable assumptions on the `Analysis` sheet.

## Using the dashboard
Open the `Dashboard` sheet and use the three yellow drop-downs (District, Residence, Sex). KPI cards, charts and key messages update. Everything is built from COUNTIF/COUNTIFS/SUM/AVERAGE formulas on named ranges (`cd_*`) pointing at `Clean_Data`, so every number can be traced. Excel slicers need a PivotTable or Table, so drop-down filters were used to keep all figures as visible formulas.

## Headline results
Measles coverage 81.2%, Penta 1 96.2%, Penta 3 85.6%, Penta 1-3 dropout 11.1%, fully immunised 65.4%. Lowest facilities: Riverbend and Hilltop (measles 59%). Rural 75% vs urban 87%; no card 65% vs card 89%.

## Method notes
Data were generated in Python (seeded for reproducibility) with realistic correlations to residence, mother's education, card availability and facility. Cleaning rules were applied programmatically and verified. The workbook was recalculated with zero formula errors, and its results were cross-checked against an independent calculation.

## Limitations
Simulated data; small facility samples (32–56 children, wide confidence intervals); cross-sectional and descriptive, so associations are not causal.
