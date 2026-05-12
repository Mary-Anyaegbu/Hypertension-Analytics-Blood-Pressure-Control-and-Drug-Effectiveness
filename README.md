# Hypertension-Analytics-Blood-Pressure-Control-and-Drug-Effectiveness

## Executive Summary
Hypertension, or high blood pressure, is a major public health challenge and a leading risk factor for cardiovascular and kidney diseases. Despite advances in treatment, many patients still experience poor blood pressure control. 

This report presents a comprehensive analysis of hypertension treatment outcomes across 350 patients at the Hypertension Cardiology Center. The findings reveal a critically high BP control failure rate of 90.57%, with 317 out of 350 patients failing to achieve controlled blood pressure within 3 months of treatment. This report identifies the key clinical predictors driving this failure rate and provides evidence-based recommendations for improving treatment outcomes.

## Problem Statement 
* What predicts BP control failure at 3 months, and how can high-risk patients be identified at the point of prescription?
* Which antihypertensive drug class delivers the best outcomes for patients with specific comorbidity profiles?

## Dataset Overview
The dataset comprises 350 patient records from the Hypertension Cardiology Center, containing 16 columns spanning patient demographics, clinical measurements, comorbidity profiles, drug prescriptions, and treatment outcomes. Each row represents one unique patient.
The columns in the data contains:
* Demographics; Patient ID, Age, Gender.
* Comorbidities; Diabetes Mellitus, Chronic Kidney Disease, Dyslipidemia, Obesity.
* Baseline Clinical metrics; Systolic and Diastolic Blood pressure.
* Outcomes; Follow Up Systolic and Diastolic Blood pressures, Bp controlled after 3 months.
* Utilization; Number of visits and Registration date.

## Data Preparation & Preprocessing

### Data Quality Assessment
Upon loading the dataset into Microsoft Power BI via Power Query, an initial data quality assessment was conducted. The dataset was found to be clean with no missing values, no duplicate records, no outliers and no errors across all 350 rows and 16 columns. 

Data types were verified and confirmed as follows:
* Numeric columns (Age, Baseline_Systolic_BP, Baseline_Diastolic_BP, Followup_Systolic_BP, Followup_Diastolic_BP, Number_of_Visits) were correctly assigned as whole numbers or decimals.
* Categorical columns (Gender, Diabetes_Mellitus, Chronic_Kidney_Disease, Dyslipidemia, Obesity, BP_Controlled_After_3_Months) were confirmed as text with Yes/No values.
* Ordinal categorical column (Medication_Adherence) was confirmed as text with three distinct values: Good, Moderate, and Poor.
* Date column (Registration_Date) was correctly formatted as a date field.

### Feature Engineering
The following calculated columns and measures were created to support the analysis:

* Age Bins: Patients were grouped into age bands (30-39, 40-49, 50-59, 60-69, 70+) to enable age distribution analysis.
* Comorbidity_Count: A calculated column counting the number of comorbid conditions per patient (0 to 4), used to analyse success rates by drug performance.
* Baseline_BP_Category: Patients were categorised into Stage 2 Hypertension and Hypertensive Crisis based on clinical thresholds.
This classification follows the guidelines of the American Heart Association (AHA), which define blood pressure categories using systolic and diastolic thresholds:
* Normal BP: Systolic <120 mmHg and Diastolic <80 mmHg
* Elevated BP: Systolic 120–129 mmHg and Diastolic <80 mmHg
* Stage 1 Hypertension: Systolic 130–139 mmHg or Diastolic 80–89 mmHg
* Stage 2 Hypertension: Systolic 140–179 mmHg or Diastolic 90–119 mmHg
* Hypertensive Crisis: Systolic ≥180 mmHg or Diastolic ≥120 mmHg

All patients in the dataset already had Stage 2 Hypertension or higher at baseline; therefore, classification was limited to Stage 2 and Hypertensive Crisis to reflect severity within this high-risk group.

## Data Modeling
To enable comorbidity-level analysis without restructuring the original dataset, a supplementary Comorbidity_Table was created using the DAX UNION function.
This table consolidates (unpivoted) the four separate Yes/No comorbidity columns into a single column structure with fields: Patient_ID, Condition, BP_Controlled, and Drug_Class. A many-to-one relationship was established with the original Hypertension_Data table via Patient_ID, with bidirectional cross-filtering enabled. DISTINCTCOUNT was applied in all measures referencing this table to prevent patient count inflation.
All subsequent analysis was conducted on the verified, prepared dataset with no further data quality interventions required.

## Data Analysis
Key metrics were derived using DAX functions, including:
* BP control failure rate
* BP control success rate
* Total patient count
* Average baseline systolic BP
* Average follow-up systolic BP. 
These metrics were then segmented across multiple dimensions to address the key business questions.
The dataset was analyzed and visualized using PowerBI.

## Dashboard Overview 







