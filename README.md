# College Scorecard EDA: Do College Costs Pay Off?

Exploratory data analysis of the U.S. Department of Education **College Scorecard** to understand how institutional characteristics (completion rate, tuition, student debt, institution type, and enrollment size) relate to graduates' median earnings 10 years after entry.

**Tools:** Python, pandas, NumPy, Matplotlib, seaborn, Jupyter

## Question

Does paying more for college lead to better financial outcomes, or do more affordable schools deliver similar results? Which institutional factors are most associated with long-term earnings?

## Data

- **Source:** [College Scorecard, Most Recent Institution-Level Data](https://collegescorecard.ed.gov/data/) (U.S. Department of Education), compiled from IPEDS, the National Student Loan Data System, and federal tax records
- **Raw data:** 6,429 institutions x 3,306 columns (not included in this repo because of its size; download it from the link above)
- **Cleaned data:** `college_scorecard_clean.csv`, with 1,938 institutions and 11 fields

## Approach

1. **Inspection:** profiled missing values (for example, 65% missing for 4-year completion rate and 42% for tuition), found privacy-suppressed ("PS") codes in median debt, and used boxplots and the IQR method to separate legitimate outliers (such as very large online universities and elite private colleges) from invalid data.
2. **Cleaning and prep:** kept 8 analysis fields, converted median debt to numeric, trimmed the top 1% of extreme values, validated value ranges, created new fields (out-of-state tuition gap, enrollment size bins, earnings-to-debt ratio), and dropped rows missing key fields as the final step.
3. **Analysis:** tested three hypotheses with Pearson correlations and regression plots, compared public, private nonprofit, and for-profit institutions with grouped medians and boxplots, and built a correlation summary.

## Key Findings

| Factor | Correlation with 10-year median earnings |
|---|---|
| Completion rate (C150_4) | 0.51 |
| In-state tuition | 0.47 |
| Median debt | 0.47 |

- **Completion rate was the strongest single predictor** of long-term earnings. Finishing a degree appears to matter more than what the degree cost.
- **Public institutions offered strong value:** median earnings of about $49,300 at a median in-state tuition of about $8,500.
- **Private nonprofits** had the highest median earnings (about $52,100) but roughly four times the public tuition (about $33,500).
- **Private for-profit institutions** had the lowest median earnings (about $40,100) despite charging about twice the public tuition.
- All findings are associational, not causal. Selectivity, program mix, region, and student characteristics likely explain much of the remaining variation.

## Files

| File | Description |
|---|---|
| `Hendricks_EDA_Project_Phase_2_v2.0.ipynb` | Full notebook: proposal, inspection, cleaning, and analysis |
| `college_scorecard_clean.csv` | Cleaned dataset used for the analysis |

## Author

Bobby Hendricks, M.S. in Data Science candidate, Northwestern University
[Portfolio](https://bobbyhendricks.netlify.app) | [LinkedIn](https://www.linkedin.com/in/bobby-h-143113252/)
