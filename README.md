# GRM & Social Support: analysis workspace (Ben)

Personal analysis workspace for the GRM in STEM study, Manuscript 2 (social support and strain as moderators of GRM -> psychological distress / turnover intention).

## Data rule

**No survey data in this repo.** `data/` is git-ignored. The cleaned dataset comes from Michele and stays outside version control. Do not paste participant-level output into issues or commits.

## Files

| File | What it is |
|---|---|
| `grm_moderation_template.Rmd` | Moderation template (PROCESS Model 1 equivalent). `PRACTICE_MODE <- TRUE` runs on Titanic data. |
| `data/` | Put `train.csv` (Titanic practice) here. Later, the clean survey file (never committed). |

## One-time package install

```r
install.packages(c("dplyr", "ggplot2", "knitr", "rmarkdown", "psych", "broom", "GPArotation"))
```

`GPArotation` is required for McDonald's omega (`psych::omega`).

## Getting the Titanic practice file

Option A (Kaggle): sign in, then download `train.csv` from https://www.kaggle.com/competitions/titanic/data and save it as `data/train.csv`. Kaggle may ask you to accept the competition rules.

Option B (no Kaggle account): in R, run
```r
install.packages("titanic")
dir.create("data", showWarnings = FALSE)
write.csv(titanic::titanic_train, "data/train.csv", row.names = FALSE)
```
Both give the same columns the template expects (`Age`, `SibSp`, `Fare`, `Sex`, `Pclass`).

## Switching to the real data

1. Set `PRACTICE_MODE <- FALSE`.
2. In the `config` chunk, replace every `TODO` with the real file name and column names from the codebook.
3. Knit. The template stops with a clear message if a column name is wrong.

## Issue conventions

Title format: `[phase] short task`, for example `[Phase 1] Verify K6 coding against codebook`.
Suggested labels: `phase-1`, `phase-2`, `phase-3`, `question-for-Michele`, `blocked`.
Put questions that need a decision from Michele in an issue labeled `question-for-Michele`, with no data values in it.
