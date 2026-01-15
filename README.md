# HEART DISEASE SURVIVAL DASHBOARD

This dashboard analyzes clinical records to visualize the relationship between biological markers (like Serum Sodium and Ejection Fraction) and patient survival rates.

Key Features:

Dynamic Survivability Metrics: Real-time calculation of survival rates across different demographics.

Risk Factor Analysis: Deep dives into how comorbidities like Diabetes and Hypertension correlate with mortality.

Patient Profiling: Visualizing age distribution vs. survival events to identify the most vulnerable age brackets.

The Technical Side (DAX Formulas): To make this dashboard interactive and accurate, I developed several custom DAX measures. Here is the logic behind the scenes:

1. TOTAL_ALIVE = CALCULATE(COUNT(heart_Disease_clinical_records_[count]),heart_Disease_clinical_records_[DEATH_EVENT]=0)

2. ALIVE % = 1-DIVIDE(SUM(heart_Disease_clinical_records_[DEATH_EVENT]),COUNT(heart_Disease_clinical_records_[count])))

3. ALIVE_AVG = CALCULATE(AVERAGE(heart_Disease_clinical_records_[age]),heart_Disease_clinical_records_[DEATH_EVENT]=0)

4. TOTAL_DEATH = CALCULATE(COUNT(heart_Disease_clinical_records_[count]),heart_Disease_clinical_records_[DEATH_EVENT]=1)

5. GENDER = IF(heart_Disease_clinical_records_[sex]=0,"FEMALE","MALE")

6. AGE_GROUP = SWITCH(TRUE(),heart_Disease_clinical_records_[age]<=40,"BELOW 40",
               heart_Disease_clinical_records_[age]>40 && heart_Disease_clinical_records_[age]<=50,"41-50",
               heart_Disease_clinical_records_[age]>50&& heart_Disease_clinical_records_[age]<=60,"51-60",
               heart_Disease_clinical_records_[age]>60&& heart_Disease_clinical_records_[age]<=70,"61-70",
               heart_Disease_clinical_records_[age]>70,"70+")
   
Insights discovered:

Patients in the 60–70 age group showed a significantly higher frequency of clinical events.

The Survival Rate across this specific dataset stands at 67.5%, providing a clear baseline for clinical assessment.


Summary of the Dataset Fields Used:
age: Patient age.

DEATH_EVENT: If the patient died during the follow-up period (1 = Yes, 0 = No).

ejection_fraction: Percentage of blood leaving the heart at each contraction.

serum_sodium: Level of sodium in the blood.

diabetes / high_blood_pressure: Comorbidity indicators.
