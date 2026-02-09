
# Develop a Computational Phenotyping Algorithm to Identify Patients with Type II Diabetes

👉 **Rendered Project Report (HTML):**  
https://erin0220.github.io/Identify-diabetic-complications-from-unstructured-clinical-notes/

---

## 📌 Project Overview
This project develops and evaluates a **computational phenotyping algorithm** to identify patients with **Type II diabetes** using structured clinical data from the `mimic3_demo` dataset.

Multiple data sources commonly used in clinical practice—diagnosis codes, laboratory values, and medications—were explored individually and in combination to assess their ability to correctly identify patients with Type II diabetes.

The goal of the project is to understand the **trade-offs between sensitivity and specificity** when using different phenotyping strategies.

---

## 🧠 Data
- **Dataset:** `mimic3_demo`
- **Gold Standard:** `course3_data.diabetes_goldstandard`
- **Key Tables Used:**
  - `DIAGNOSES_ICD`
  - `LABEVENTS`
  - `D_LABITEMS`
  - `PRESCRIPTIONS`

The gold-standard dataset labels patients as having Type II diabetes (`DIABETES = 1`) or not (`DIABETES = 0`).

---

## ⚙️ Phenotyping Approaches Evaluated

### 1️⃣ ICD-9 Diagnosis Codes
- Evaluated ICD-9 code **250.00** and expanded sets of Type II diabetes ICD codes
- Strength: high specificity
- Limitation: lower sensitivity

---

### 2️⃣ Laboratory Data
- Hemoglobin A1c (HbA1c)
- Mean blood gas glucose ≥ 200 mg/dL
- Strength: clinically meaningful
- Limitation: incomplete coverage across patients

---

### 3️⃣ Medication Data
- Metformin
- Insulin
- Combination of metformin and insulin
- Strength: high specificity
- Limitation: low sensitivity due to inpatient insulin use patterns

---

### 4️⃣ Combined Rules
The following composite rules were evaluated:
- ICD **OR** glucose ≥ 200 **OR** insulin
- ICD **AND** glucose ≥ 200 **AND** insulin
- Insulin **AND** (ICD **OR** glucose ≥ 200)

These combinations demonstrated important trade-offs:
- OR-based rules improved sensitivity
- AND-based rules improved specificity

---

## 📊 Evaluation
All phenotyping rules were evaluated against the gold standard using **confusion matrices**, reporting:
- Sensitivity
- Specificity
- Accuracy

This analysis highlights that no single data source is sufficient and that **rule-based combinations** can significantly alter model performance depending on the intended use case.

---

## 🛠 Tools & Technologies
- R
- R Markdown
- tidyverse
- caret
- BigQuery (Google Cloud)
- SQL
- Regular expressions

---

## 📚 Course Context
This project was completed as part of a **Clinical Data Science / Health Informatics** course focused on:
- Computational phenotyping
- Use of structured EHR data
- Clinical reasoning in algorithm design
- Understanding performance trade-offs in real-world data

---

## 📝 Key Takeaways
- ICD codes alone are highly specific but miss many true cases
- Laboratory and medication data add valuable signal but are incomplete
- Combining multiple data sources improves phenotype robustness
- The optimal rule depends on whether sensitivity or specificity is prioritized

---
