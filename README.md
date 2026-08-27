# Chronic Kidney Disease Diagnostic Gap in the US (NHANES 2007–2018)

Analysis of the gap between biological evidence of Chronic Kidney Disease (CKD) and
physician-diagnosed / self-reported awareness, across six NHANES survey cycles
(2007–2018, ~10 years) in the U.S. adult population.

Team project for the **Health Data Visualization** course, MSc in Health Data Science (URV).
Authors: Gabriel Torres, Pablo Longán, David Hidalgo Fàbregas.

## Motivation

CKD is often asymptomatic in its early stages, and a large share of at-risk individuals
are never diagnosed until the disease has progressed. This project quantifies that
diagnostic gap in a nationally representative U.S. sample and investigates which
socioeconomic and demographic factors are associated with it.

## Data

U.S. National Health and Nutrition Examination Survey (NHANES), six two-year cycles:

| Cycle | Files used |
|---|---|
| 2007–2008 | `DEMO_E`, `BIOPRO_E`, `ALB_CR_E`, `HIQ_E`, `KIQ_U_E` |
| 2009–2010 | `DEMO_F`, `BIOPRO_F`, `ALB_CR_F`, `HIQ_F`, `KIQ_U_F` |
| 2011–2012 | `DEMO_G`, `BIOPRO_G`, `ALB_CR_G`, `HIQ_G`, `KIQ_U_G` |
| 2013–2014 | `DEMO_H`, `BIOPRO_H`, `ALB_CR_H`, `HIQ_H`, `KIQ_U_H` |
| 2015–2016 | `DEMO_I`, `BIOPRO_I`, `ALB_CR_I`, `HIQ_I`, `KIQ_U_I` |
| 2017–2018 | `DEMO_J`, `BIOPRO_J`, `ALB_CR_J`, `HIQ_J`, `KIQ_U_J` |

Datasets: Demographics (`DEMO`), Standard Biochemistry Profile (`BIOPRO`), Albumin &
Creatinine — Urine (`ALB_CR`), Health Insurance (`HIQ`), and Kidney Conditions —
Urology questionnaire (`KIQ_U`).

## Methods

- Harmonized the 6 cycles into a single adult cohort via multi-file joins on `SEQN`.
- Derived eGFR (CKD-EPI) and urine albumin-to-creatinine ratio (uACR), and staged CKD
  risk following **KDIGO guideline** thresholds into a binary high-risk biomarker.
- Compared biomarker-positive status against self-reported physician diagnosis
  (`KIQ_U` questionnaire) to quantify the diagnostic gap.
- Chi-square tests and odds ratios across insurance status, poverty-income ratio,
  education, and race/ethnicity to identify significant associated factors.
- Explanatory infographic (Python, matplotlib/seaborn) designed for a non-technical,
  health-administrator audience.

## Key findings

- ~**6%** of the sampled population is at high biological risk of CKD.
- ~**74%** of those high-risk individuals are undiagnosed or unaware of their condition.
- **Lack of health insurance** was the only factor with a statistically significant
  association with the diagnostic gap (chi-square / odds ratio testing); poverty level
  and race/ethnicity showed a compounding, intersectional pattern in insurance coverage.
- The diagnostic gap has **narrowed slowly** over the 2007–2018 period but remains large.

![CKD diagnostic gap infographic](Infography.png)

## Repository structure

```
.
├── Exploratory_analysis.ipynb   # Full analysis: data loading, cleaning, biomarker
│                                 # derivation, statistical testing, plots
├── Exploratory_analysis.html    # Rendered, read-only export of the notebook
├── Abstract.html                 # Project abstract / summary write-up
├── Infography.png                # Final explanatory infographic
└── README.md
```

## Tech stack

Python · pandas · NumPy · matplotlib · seaborn · scipy.stats · Jupyter

## Data source & license

Data: NHANES, National Center for Health Statistics (NCHS), CDC — public-use,
de-identified survey microdata. This repository contains only code and derived
outputs (notebook, figures, abstract); no raw NHANES files are redistributed here.
