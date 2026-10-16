# Race/ethnicity, county income, and survival in adult acute lymphoblastic leukemia (SEER, 2010-2021)

An independent analysis of whether race/ethnicity and neighborhood income are associated with survival after a leukemia diagnosis, and whether those associations change over follow-up.

**Full report:** open `analysis.html` (rendered from `analysis.Rmd`).

## Question

Is the overall survival of U.S. adults over the age of 20 diagnosed with acute lymphoblastic leukemia (ALL) between 2010 and 2021 associated with race/ethnicity and county-level income levels, and do these relationships stay constant 24 months after diagnosis?

## Main findings

- **County income.** Patients living in low-income counties were assosiated with a 33% higher hazard of death in comparain to high-income counties (HR 1.33). This gap was mostly concentrated from 0-24 months, and was no longer detectable after 24 months.
- **Race/ethnicity.** After adjusting for age, sex, and county income, Hispanic and Black patients had a higher hazard of death than non-Hispanic White patients (HR 1.20 and 1.22). These gaps grew after 24 months (HR 1.15 to 1.50).

These are associations in registry data that lack treatment information, and income is measured at the county level, not for individual patients. This is an exploratory analysis.

![Forest plot](figures/forest_plot.png)

## Data

The cohort data comes from SEER Research Data from the National Cancer Institute and was exported through SEER**Stat. SEER's data use agreement does not allow redistribution of the data, so to reproduce the analysis, request data access through the SEER directory, then export a case listing with the following fields: sex, year of diagnosis, race, recode, median household income, SEER cause-specific death classification, survival months, and vital status recode. 

## Methods in brief

- Cohort: adults over the age of 20 diagnosed with acute lymphoblastic leukemia, diagnosed between 2010 and 2021.
- Kaplan-Meier curves by race/ethnicity.
- Cox proportional hazards models adjusted for sex and stratified by age group.
- Effects are reported separately for 0-24 months and 24+ months as the proportional-hazards assumption failed. 
- In current SEER releases, individual insurance data is not available, so county income-level was used as the socioeconomic factor. 

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

The use of county-level income as a socioeconomic factor, as it is an area-level rather than looking at the individual patients. Results after 24 months are conditional on the survival of at least 24 months. See the Limitations section of the report for a full list.
