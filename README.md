# 🩺 Healthcare Analytics: Stroke Risk Prediction Using Business Intelligence & Python

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-orange.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green.svg)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-red.svg)
![Gradio](https://img.shields.io/badge/Gradio-Web%20App-yellow.svg)

## 📌 Project Overview
This project focuses on analyzing a comprehensive medical and demographic dataset of patients using Python to extract clinically meaningful insights regarding stroke occurrence. The analysis encompasses data cleaning, pre-processing, feature engineering, exploratory data analysis (EDA), statistical analysis, and data visualization to identify critical health patterns, thresholds, and risk factors contributing to stroke events.

The goal is to transform raw medical records into actionable clinical insights that support healthcare providers in early identification, risk stratification, and preventive intervention strategies.

---

## 📊 Dataset Description
* **Source:** Stroke Risk Clinical Dataset (`stroke_data_no_sno.csv`) via Mendeley Data Repository.
* **Timeline / Year:** Data collected during the period 2026.
* **Size:** 22,420 rows × 13 primary raw attributes (16 columns after feature engineering).
* **Anonymization:** All personal identifiers and regional details are fully removed to protect patient privacy.

### Primary Attributes
| Attribute | Nature | Description |
| :--- | :--- | :--- |
| `Id` | Unique Identifier | Tracking number for each patient. |
| `Gender` | Demographic | Male, Female, or Other. |
| `Age` | Demographic | Patient age in years. |
| `Hypertension` | Clinical Indicator | High blood pressure history (0 = No, 1 = Yes). |
| `heart_disease` | Clinical Indicator | Pre-existing heart conditions (0 = No, 1 = Yes). |
| `ever_married` | Lifestyle | Marital status history (Yes or No). |
| `work_type` | Lifestyle | Employment category (Private, Govt_job, Self-employed, etc.). |
| `Residence_type` | Environmental | Living environment category (Urban or Rural). |
| `avg_glucose_level` | Clinical Metric | Average blood glucose level (mg/dL). |
| `Bmi` | Clinical Metric | Body Mass Index (kg/m²). |
| `smoking_status` | Behavioral | Smoking history (never smoked, smokes, formerly smoked, Unknown). |
| `Stroke` | Target Variable | Indicates stroke occurrence (0 = No, 1 = Yes). |

---

## 🛠️ Tools & Technologies Used
* **Environment:** Google Colab
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn, Plotly Express
* **User Interface / Dashboard:** Gradio (Web Application UI featuring live KPI cards, interactive filters, and dynamic charts)

---

## 💻 Web Application Features (Gradio UI)
The project includes an interactive web dashboard built with **Gradio** that provides:
* **Interactive Filtering:** Filter data dynamically based on Age, Glucose levels, BMI, and Smoking Status.
* **Live KPI Cards:** Displays real-time updates for Total Patients, Average Glucose, Average BMI, and Overall Stroke Rate.
* **Visual Dashboards:** Renders dynamic charts (e.g., Risk Distribution, Co-morbidity Analysis) based on selected user inputs.


---

## 🔄 Data Pre-Processing & Feature Engineering

### 1. Data Cleaning
* **Redundant Columns:** Removed non-predictive identifiers (e.g., `S.no`).
* **Standardization:** Integer conversion using `np.ceil` for continuous age values.
* **String Formatting:** Cleaned whitespace, replaced special characters (`_`, `-`), and converted text labels using `.str.title()`.
* **Missing Value Imputation:** Imputed missing `BMI` values using the **median BMI grouped by Gender and Age**.
* **Label Mapping:** Converted binary variables (0/1) to human-readable strings (`Yes`/`No`, `Stroke`/`No Stroke`).

### 2. Feature Engineering
* **`Age_Group`:** Binned into `Children` (≤17), `Adults` (17-45), `Middle Aged` (45-60), and `Senior Citizens` (60+).
* **`BMI_Category`:** Segmented into `Underweight` (<18.5), `Normal` (18.5-24.9), `Overweight` (24.9-29.9), and `Obese` (≥29.9).
* **`Diabetes_level`:** Categorized into `Normal` (<99), `Prediabetes` (99-125), and `Diabetes` (≥125).
* **`Risk_Factor`:**
  * **High Risk:** Hypertension = 'Yes' AND Heart Disease = 'Yes'.
  * **Moderate Risk:** Age > 50 AND (Hypertension = 'Yes' OR Heart Disease = 'Yes').
  * **Low Risk:** Neither condition satisfied.

---

## 📈 Key Findings & Insights

### 1. Key Performance Indicators (KPIs)
* **Total Patients Evaluated:** 22,420
* **Overall Stroke Prevalence Rate:** **4.44%** (996 positive cases)
* **Average Glucose Level:** 105.93 mg/dL
* **Average BMI:** 28.85 kg/m²

### 2. Clinical Risk Thresholds
* **Glucose Tipping Point ($\approx 140\text{ mg/dL}$):** Stroke prevalence spikes dramatically when glucose levels exceed $140\text{ mg/dL}$, reaching up to **16.0%** in severe hyperglycemia ($>180\text{ mg/dL}$).
* **BMI Risk Accentuation ($\ge 30\text{ kg/m}^2$):** Crossing into Obesity Class I doubles stroke frequency compared to normal baselines.

### 3. Co-morbidity Multiplier
* **Healthy Baseline:** 3.1% stroke rate.
* **Hypertension Only:** 11.2% stroke rate (3.6x increase).
* **Heart Disease Only:** 15.0% stroke rate (4.9x increase).
* **Both Conditions Concurrent:** **19.0% stroke rate** (6.1x increase over baseline).

### 4. Demographic & Lifestyle Patterns
* **Age Exponential Trend:** Senior citizens (>75 years) exhibit a **19.3%** stroke rate compared to 0.1% in under-30 cohorts.
* **Urban vs. Rural Disparity:** Urban areas show higher middle-aged risk due to stress/diet, while rural areas peak in elderly risk (**19.3%**) due to healthcare access barriers.
* **Behavioral Drivers:** Formerly smoked patients exhibit a **7.2%** stroke rate, reflecting permanent microvascular damage.

---

## 🎯 Analytical Framework
1. **Descriptive Analysis:** Evaluated cohort baselines and overall stroke rate (4.44%).
2. **Diagnostic Analysis:** Pinpointed risk acceleration thresholds ($140\text{ mg/dL}$ glucose and co-morbidities elevating risk to 19.0%).
3. **Predictive Analysis:** Identified high-vulnerability segments (rural elderly patients with high blood sugar).
4. **Prescriptive Analysis:** Outlined targeted mobile health clinics, automated EHR watchlists, and combined metabolic care plans.

---

## 🚀 Strategic Recommendations & Action Plan
* **Automated EHR Triage:** Implement real-time alerts flagging patients crossing $140\text{ mg/dL}$ glucose or presenting concurrent hypertension and heart disease.
* **Rural Telemedicine Hubs:** Deploy mobile diagnostic units to rural areas for screening adults aged 50+.
* **Integrated Metabolic Protocols:** Develop dual-treatment plans addressing both blood glucose and body weight simultaneously.

---

## 🔮 Future Enhancements
* Incorporate real-time ML models (XGBoost / Neural Networks) with **Explainable AI (SHAP/LIME)**.
* Expand data features to include **HbA1c trajectories, lipid panels, and IoT wearable tracking**.
