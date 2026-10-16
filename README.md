# Race/ethnicity, county income, and survival in adult leukemia (SEER, 2010-2021)

An independent analysis of whether race/ethnicity and neighborhood income are associated with survival after a leukemia diagnosis, and whether those associations change over follow-up.

**Full report:** open `analysis.html` (rendered from `analysis.Rmd`).

## Question

Among U.S. adults diagnosed with leukemia **[CONFIRM subtype]** between 2010 and 2021, is overall survival associated with race/ethnicity and county-level median household income, and do those associations stay constant over time?

## Main findings

**[Fill in after you finish the Discussion section of the report. Write 3-4 plain sentences with the real numbers from the forest plot. Do not claim anything the intervals don't support.]**

![Forest plot](figures/forest_plot.png)

## Data

SEER Research Data (National Cancer Institute), exported with SEER*Stat. SEER's data use agreement does not allow redistributing the data, so it is **not** included in this repository. To reproduce the analysis, request access at https://seer.cancer.gov/data/access.html, then export a case listing with these fields: sex, year of diagnosis, race and origin recode, age recode, median household income (inflation adjusted to 2022), SEER cause-specific death classification, survival months, and vital status recode. Save it as `data/seer1.txt` (tab-delimited, labels without quotes, variable names before data).

## Methods in brief

- Cohort: adults aged 20+, diagnosed 2010-2021, exported from 17 SEER registries.
- Kaplan-Meier curves by race/ethnicity.
- Cox proportional hazards models adjusted for sex and stratified by age group.
- The proportional-hazards assumption failed, so effects are reported separately for 0-24 and 24+ months after diagnosis (an exploratory cut point chosen after inspecting residual plots).
- Individual insurance status is not available in current SEER releases, so county income is used as the socioeconomic measure.

## Repository structure

```
analysis.Rmd     # full analysis (data cleaning, models, figures)
analysis.html    # rendered report
figures/         # plots used in the report
output/          # summary tables (CSV)
data/            # not tracked; place seer1.txt here
```

## How to reproduce

1. Obtain the data as described above and place it in `data/seer1.txt`.
2. Install the R packages `tidyverse`, `survival`, `ggsurvfit`, `broom`, and `rmarkdown`.
3. Open `analysis.Rmd` in RStudio and click Knit.

## Limitations

County income is an area-level measure, the data lack treatment and clinical information, results after 24 months are conditional on survival to that point, and the time split was chosen after viewing the data. See the Limitations section of the report for the full list.

## Transparency note

I designed the question, exported the data, and wrote the interpretation. The analysis code was developed with the help of Claude (Anthropic) while I was learning R. I'm working through R fundamentals in parallel and can walk through any part of the code.

## Author

Shane, undergraduate, pre-medical track. Contact: **[your email]**
