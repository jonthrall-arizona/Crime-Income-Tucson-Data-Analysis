# Income and Crime in Tucson: Examining Data-Driven Insights by Ward

A data science project examining the relationship between neighborhood income levels and crime rates across Tucson, Arizona's six wards, built for CSC 380 (Principles of Data Science) at the University of Arizona.

**Authors:** Jon Thrall, Ming Wang, Jaidon McIntosh-Cassa

## Overview

This project investigates whether neighborhood-level economic indicators — a wealth index and total household counts — are associated with crime rates across Tucson, and how well those indicators alone can explain or predict differences in crime between neighborhoods. The analysis combines descriptive statistics, data visualization, and two predictive modeling approaches to explore this relationship carefully and report results in correlational, not causal, terms.

## What's in this repo

- **`Report.pdf`** — the full written report: introduction, related works, methodology, data visualization, both models, results, limitations, and references.
- **`TPD.ipynb`** — the complete analysis notebook: data cleaning, merging, visualization, and both models, runnable end to end.

## Data

All data comes from the City of Tucson's public GIS data hub. The raw CSVs used in this analysis are included in this repo:

| File | Description |
|---|---|
| `crimes.csv` | Tucson Police reported crime incidents, including ward, neighborhood, crime type, and time of occurrence. |
| `arrests.csv` | Tucson Police arrest records by neighborhood, used to compute crime counts per neighborhood for the predictive models. |
| `income.csv` | Neighborhood-level socioeconomic data, including a wealth index and total household counts, used as the model features. |

Source: [City of Tucson GIS Data](https://gisdata.tucsonaz.gov/) — Tucson Police Reported Crimes and neighborhood income/household datasets.

## Methods

- **Data cleaning & integration:** merging crime records with income/household data on shared neighborhood identifiers; handling missing values and inconsistent timestamps.
- **Descriptive visualization:** wealth index vs. household distribution by ward, hourly crime patterns by ward, and crime type breakdown by ward.
- **Model 1 — Linear Regression:** predicts a neighborhood's total crime count from Wealth Index and Total Households. Achieves an R² of 0.20 (MSE of 933,382 vs. a baseline of 1,167,674).
- **Model 2 — Logistic Regression:** classifies neighborhoods as high- or low-crime (relative to the median) using the same two features. Achieves 81% accuracy and an AUC of 0.93.

## A note on scope

An earlier version of this analysis also included neighborhood-level race and ethnicity demographic data as model features. That data has been removed. Race and ethnicity were never the variables this project set out to study, and using them as predictive inputs for a crime-classification model risked implying a claim the data can't responsibly support. The version in this repo uses only income and household data, consistent with the project's original hypothesis about economic conditions, and reports every finding in correlational terms with an explicit limitations discussion (ecological fallacy, reporting/policing bias in crime data, and unaccounted-for confounding variables).

## Key takeaway

Income and household data alone are moderately useful for distinguishing higher-crime from lower-crime neighborhoods in broad terms (Model 2), but far less able to predict the exact volume of crime in a given neighborhood (Model 1's modest R²). The results point toward economic conditions as one relevant factor among many — not a complete explanation, and not a basis for predicting or profiling individual neighborhoods or residents.

## Tools

Python, pandas, NumPy, scikit-learn, seaborn, matplotlib.
