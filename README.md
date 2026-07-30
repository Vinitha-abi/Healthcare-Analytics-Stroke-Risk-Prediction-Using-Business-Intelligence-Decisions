# 🩺 Healthcare Analytics: Stroke Risk Prediction Using Business Intelligence & Python

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-orange.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green.svg)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-red.svg)
![Gradio](https://img.shields.io/badge/Gradio-Web%20App-yellow.svg)

## 📌 Project Overview
This project focuses on analyzing a comprehensive medical and demographic dataset of patients using Python to extract clinically meaningful insights regarding stroke occurrence[cite: 1]. The analysis encompasses data cleaning, pre-processing, feature engineering, exploratory data analysis (EDA), statistical analysis, and data visualization to identify critical health patterns, thresholds, and risk factors contributing to stroke events[cite: 1].

The goal is to transform raw medical records into actionable clinical insights that support healthcare providers in early identification, risk stratification, and preventive intervention strategies[cite: 1].

---

## 📊 Dataset Description
* **Source:** Stroke Risk Clinical Dataset (`stroke_data_no_sno.csv`) via Mendeley Data Repository[cite: 1].
* **Timeline / Year:** Data collected during the period 2026[cite: 1].
* **Size:** 22,420 rows × 13 primary raw attributes (16 columns after feature engineering)[cite: 1].
* **Anonymization:** Hospital names and geographic details are fully removed for patient privacy[cite: 1].

### Primary Attributes
| Attribute | Nature | Description |
| :--- | :--- | :--- |
| `Id` | Unique Identifier | Tracking number for each patient[cite: 1]. |
| `Gender` | Demographic | Male, Female, or Other[cite: 1]. |
| `Age` | Demographic | Patient age in years[cite: 1]. |
| `Hypertension` | Clinical Indicator | High blood pressure history (0 = No, 1 = Yes)[cite: 1]. |
| `heart_disease` | Clinical Indicator | Pre-existing heart conditions (0 = No, 1 = Yes)[cite: 1]. |
| `ever_married` | Lifestyle | Marital status history (Yes or No)[cite: 1]. |
| `work_type` | Lifestyle | Employment category (Private, Govt_job, Self-employed, etc.)[cite: 1]. |
| `Residence_type` | Environmental | Living environment category (Urban or Rural)[cite: 1]. |
| `avg_glucose_level` | Clinical Metric | Average blood glucose level (mg/dL)[cite: 1]. |
| `Bmi` | Clinical Metric | Body Mass Index (kg/m²)[cite: 1]. |
| `smoking_status` | Behavioral | Smoking history (never smoked, smokes, formerly smoked, Unknown)[cite: 1]. |
| `Stroke` | Target Variable | Indicates stroke occurrence (0 = No, 1 = Yes)[cite: 1]. |

---

## 🛠️ Tools & Technologies Used
* **Environment:** Google Colab[cite: 1]
* **Data Manipulation:** Pandas, NumPy[cite: 1]
* **Data Visualization:** Matplotlib, Seaborn, Plotly Express[cite: 1]
* **User Interface / Dashboard:** Gradio (Web Application UI)[cite: 1]

---

## 🔄 Data Pre-Processing & Feature Engineering

### 1. Data Cleaning
* **Redundant Columns:** Removed non-predictive identifiers (e.g., `S.no`)[cite: 1].
* **Standardization:** Integer conversion using `np.ceil` for continuous age values[cite: 1].
* **String Formatting:** Cleaned whitespace, replaced special characters (`_`, `-`), and converted text labels using `.str.title()`[cite: 1].
* **Missing Value Imputation:** Imputed missing `BMI` values using the **median BMI grouped by Gender and Age**[cite: 1].
* **Label Mapping:** Converted binary variables (0/1) to human-readable strings (`Yes`/`No`, `Stroke`/`No Stroke`)[cite: 1].

### 2. Feature Engineering
* **`Age_Group`:** Binned into `Children` (≤17), `Adults` (17-45), `Middle Aged` (45-60), and `Senior Citizens` (60+)[cite: 1].
* **`BMI_Category`:** Segmented into `Underweight` (<18.5), `Normal` (18.5-24.9), `Overweight` (24.9-29.9), and `Obese` (≥29.9)[cite: 1].
* **`Diabetes_level`:** Categorized into `Normal` (<99), `Prediabetes` (99-125), and `Diabetes` (≥125)[cite: 1].
* **`Risk_Factor`:**
  * **High Risk:** Hypertension = 'Yes' AND Heart Disease = 'Yes'[cite: 1].
  * **Moderate Risk:** Age > 50 AND (Hypertension = 'Yes' OR Heart Disease = 'Yes')[cite: 1].
  * **Low Risk:** Neither condition satisfied[cite: 1].

---

## 📈 Key Findings & Insights

### 1. Key Performance Indicators (KPIs)
* **Total Patients Evaluated:** 22,420[cite: 1]
* **Overall Stroke Prevalence Rate:** **4.44%** (996 positive cases)[cite: 1]
* **Average Glucose Level:** 105.93 mg/dL[cite: 1]
* **Average BMI:** 28.85 kg/m²[cite: 1]

### 2. Clinical Risk Thresholds
* **Glucose Tipping Point ($\approx 140\text{ mg/dL}$):** Stroke prevalence spikes dramatically when glucose levels exceed $140\text{ mg/dL}$, reaching up to **16.0%** in severe hyperglycemia ($>180\text{ mg/dL}$)[cite: 1].
* **BMI Risk Accentuation ($\ge 30\text{ kg/m}^2$):** Crossing into Obesity Class I doubles stroke frequency compared to normal baselines[cite: 1].

### 3. Co-morbidity Multiplier
* **Healthy Baseline:** 3.1% stroke rate[cite: 1].
* **Hypertension Only:** 11.2% stroke rate (3.6x increase)[cite: 1].
* **Heart Disease Only:** 15.0% stroke rate (4.9x increase)[cite: 1].
* **Both Conditions Concurrent:** **19.0% stroke rate** (6.1x increase over baseline)[cite: 1].

### 4. Demographic & Lifestyle Patterns
* **Age Exponential Trend:** Senior citizens (>75 years) exhibit a **19.3%** stroke rate compared to 0.1% in under-30 cohorts[cite: 1].
* **Urban vs. Rural Disparity:** Urban areas show higher middle-aged risk due to stress/diet[cite: 1], while rural areas peak in elderly risk (**19.3%**) due to healthcare access barriers[cite: 1].
* **Behavioral Drivers:** Formerly smoked patients exhibit a **7.2%** stroke rate, reflecting permanent microvascular damage[cite: 1].

---

## 🎯 Analytical Framework
1. **Descriptive Analysis:** Evaluated cohort baselines and overall stroke rate (4.44%)[cite: 1].
2. **Diagnostic Analysis:** Pinpointed risk acceleration thresholds ($140\text{ mg/dL}$ glucose and co-morbidities elevating risk to 19.0%)[cite: 1].
3. **Predictive Analysis:** Identified high-vulnerability segments (rural elderly patients with high blood sugar)[cite: 1].
4. **Prescriptive Analysis:** Outlined targeted mobile health clinics, automated EHR watchlists, and combined metabolic care plans[cite: 1].

---

## 🚀 Strategic Recommendations & Action Plan
* **Automated EHR Triage:** Implement real-time alerts flagging patients crossing $140\text{ mg/dL}$ glucose or presenting concurrent hypertension and heart disease[cite: 1].
* **Rural Telemedicine Hubs:** Deploy mobile diagnostic units to rural areas for screening adults aged 50+[cite: 1].
* **Integrated Metabolic Protocols:** Develop dual-treatment plans addressing both blood glucose and body weight simultaneously[cite: 1].

---

## 🔮 Future Enhancements
* Incorporate real-time ML models (XGBoost / Neural Networks) with **Explainable AI (SHAP/LIME)**[cite: 1].
* Expand data features to include **HbA1c trajectories, lipid panels, and IoT wearable tracking**[cite: 1].
