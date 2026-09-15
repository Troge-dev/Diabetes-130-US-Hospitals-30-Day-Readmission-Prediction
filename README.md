# 30-Day Hospital Readmission Risk Prediction
**DS312 Data Mining and Applications — Laboratory 2**

## Overview
This repository contains the structured data cleaning, preprocessing, exploratory data analysis (EDA), and machine learning pipeline for predicting 30-day readmission risk among diabetic patients using the **Diabetes 130-US Hospitals (1999–2008)** dataset.

## Clinical Context & Motivation
Under the CMS **Hospital Readmissions Reduction Program (HRRP)**, hospitals face financial penalties for unplanned 30-day patient readmissions. Identifying high-risk diabetic patients prior to discharge allows clinical care teams to coordinate targeted interventions, optimize discharge planning, and reduce readmission rates.

## Problem Formulation
* **Domain:** Clinical Healthcare & Hospital Inpatient Operations
* **Dataset:** 101,766 clinical encounters across 130 US hospitals
* **Target Variable:** `readmitted` (Binarized: `1` for `<30` days, `0` for `>30` days or `NO`)
* **Problem Type:** Supervised Binary Classification
* **Target Model:** Regularized Logistic Regression (L2 / Elastic-Net)

## Project Structure
```
├── data/              # Raw and processed datasets (ignored by git)
├── notebooks/         # Jupyter notebooks for EDA, preprocessing, and modeling
├── output/            # Model checkpoints, evaluation metrics, and figures
├── reports/           # Analysis reports and presentation artifacts
├── .gitignore         # Excluded files, data files, and local prompts
└── README.md          # Project overview and documentation
```
