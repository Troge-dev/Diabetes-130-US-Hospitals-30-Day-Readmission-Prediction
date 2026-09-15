# 30-Day Hospital Readmission Risk Prediction
### Structured Data Cleaning, Preprocessing & EDA Storytelling Pipeline

> **Course:** DS312 — Data Mining and Applications  
> **Instructor:** Nicole S. Menorias  
> **Academic Activity:** Module 4 — Preprocessing for Structured Data | Laboratory 2: Structured Data Cleaning and EDA Storytelling Report  
> **Repository:** [Troge-dev/Diabetes-130-US-Hospitals-30-Day-Readmission-Prediction](https://github.com/Troge-dev/Diabetes-130-US-Hospitals-30-Day-Readmission-Prediction)

---

## 1. Academic Fulfillment & Course Context

This project is submitted in partial fulfillment of the requirements for **DS312: Data Mining and Applications**, specifically adhering to the activity guidelines outlined in **Module 4: Preprocessing for Structured Data (Laboratory 2: Structured Data Cleaning and EDA Storytelling Report)**.

The primary objective is to take a high-dimensional, structurally messy clinical dataset, diagnose its data-generating and missingness mechanisms, clean and preprocess it rigorously with defensible justifications, and perform diagnostic EDA and statistical inference to generate a model-ready feature space for predictive data mining.

---

## 2. Laboratory 2 Activity Alignment & Specification

The repository is structured to directly fulfill all requirements specified in the **Module 4 Activity Reference**:

| Lab Requirement | Implementation in Repository | Methodological Rationale |
| :--- | :--- | :--- |
| **Step 0: Goal & Model Definition** | Dichotomized 30-day readmission risk (`readmitted` < 30 days vs. > 30 / NO); Supervised Binary Classification with Regularized Logistic Regression (L2 / Elastic-Net). | Model weights are sensitive to feature scales and multicollinearity, dictating strict scaling and encoding choices. |
| **Step 1: Missing Data Diagnostics** | Systematic analysis classifying missingness into **MCAR**, **MAR**, or **MNAR** with statistical evidence and domain grounding. | Distinguish administrative omissions from clinical missingness (e.g., `weight` MNAR dropped vs. `medical_specialty` MAR indicator imputed). |
| **Step 2: Before & After Validation** | Explicit before-and-after summary statistics tables (means, medians, IQRs, variances, and null percentages). | Validates that data preprocessing preserves sample integrity and does not introduce synthetic distributional distortion. |
| **Step 3: Scaling & Categorical Encoding** | Per-feature transformation justified by the target model: `RobustScaler` for skewed counts, `StandardScaler` for clinical vitals/labs, One-Hot Encoding (`drop_first=True`) for nominal features. | Prevents gradient domination in regularized regression while avoiding dummy variable trap. |
| **Step 4: Exploratory Data Analysis (EDA)** | Univariate distributions, bivariate cross-analyses against 30-day readmission, and correlation heatmaps. | Evaluates feature balance, clinical separation, and multicollinearity before downstream modeling. |
| **Step 5: Hypothesis Testing & Assumptions** | Formal two-sample hypothesis test with full assumption verification (normality / variance homogeneity) and plain-language clinical interpretation. | Quantifies statistical significance of key clinical predictors against readmission outcomes. |
| **Step 6: Non-Technical Narrative** | 5–8 bullet executive storytelling summary translating statistical findings into actionable healthcare operational insights. | Enables non-technical clinical directors and hospital administrators to implement findings. |

---

## 3. Dataset Profile & Scope Management

* **Dataset:** [Diabetes 130-US Hospitals (1999–2008)](https://www.kaggle.com/datasets/anushrevankar/uci-diabetes-130-us-hospitals-dataset) (UCI Machine Learning Repository)
* **Domain:** Clinical Healthcare & Hospital Inpatient Operations
* **Encounter Volume:** 101,766 clinical encounters across 130 US hospitals
* **Raw Attributes:** 50 clinical, demographic, medication, and operational features
* **Missing Sentinel:** Question marks (`'?'`) systematically converted to `np.nan` prior to diagnostics
* **Longitudinal Scope Management:** Retained only the **first encounter per unique patient (`patient_nbr`)** to prevent patient-level auto-correlation bias (~70,442 unique patient encounters).
* **Terminal Discharge Exclusion:** Excluded deceased patients and hospice discharges (`discharge_disposition_id` 11, 13, 14, 19, 20, 21) who are not eligible for 30-day readmission.

---

## 4. Deliverables

* **Deliverable 1 — Lab 2 Notebook (`notebooks/`):**
  * End-to-end runnable Python Jupyter Notebook implementing the complete inspect → clean → transform → explore pipeline.
  * Explicit markdown justifications accompanying each transformation step.
  * Final model-ready dataset output.
* **Deliverable 2 — 1-Page Summary Report (`reports/`):**
  * Concise executive summary featuring project goal, key cleaning decisions, 2–3 hero visualizations, hypothesis test findings, and the 5–8 bullet non-technical narrative.

---

## 5. Repository Structure

```
├── data/              # Raw and preprocessed datasets (git-ignored, kept via .gitkeep)
├── notebooks/         # Lab 2 Jupyter Notebooks for cleaning, scaling, and EDA
├── output/            # Generated figures, plots, and processed modeling exports
├── reports/           # Deliverable 2: 1-Page Summary Report & artifacts
├── ignored stuff/     # Local development prompts, instructions, and scratch files (git-ignored)
├── .gitignore         # Ignores 'ignored stuff/', large data, virtual environments, and caches
└── README.md          # Project specification, course alignment, and documentation
```

---

## 6. Academic References & Methodological Foundations

1. **Course Curriculum:** *DS312 Data Mining and Applications*, Module 4: Preprocessing for Structured Data. Instructor: Nicole S. Menorias.
2. **Data Mining Principles:** Han, J., Kamber, M., & Pei, J. (2011). *Data Mining: Concepts and Techniques* (3rd ed.). Morgan Kaufmann. (Chapter 3: Data Preprocessing).
3. **Missing Data Theory:** Rubin, D. B. (1976). *Inference and Missing Data*. *Biometrika*, 63(3), 581–592.
4. **Statistical Diagnostics:** Little, R. J. A., & Rubin, D. B. (2019). *Statistical Analysis with Missing Data* (3rd ed.). John Wiley & Sons.
5. **Exploratory Data Analysis:** Tukey, J. W. (1977). *Exploratory Data Analysis*. Addison-Wesley.
6. **Hypothesis Testing Assumptions:** Field, A. (2018). *Discovering Statistics Using IBM SPSS Statistics* (5th ed.). SAGE Publications.
