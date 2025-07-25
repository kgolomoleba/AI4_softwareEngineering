
# AI for Software Engineering  
## Assignment: Understanding the AI Development Workflow

---

### Course Details  
- **Course:** AI for Software Engineering  
- **Duration:** 7 days  
- **Total Points:** 100

---

## Objective & Guidelines

This assignment tests your ability to apply the **AI Development Workflow** to a real-world problem. You will demonstrate understanding of key stages—from problem definition to deployment—and critically analyze challenges and ethical considerations.

- Work in peer groups.  
- Submit a PDF report (5–10 pages excluding diagrams) with section headings and references.  
- Provide a GitHub repository with all code well-commented.  
- Share the PDF as an article in the PLP Academy Community.

---

## Grading Rubric

| Criterion           | Weight  | Description                                  |  
|---------------------|---------|----------------------------------------------|  
| Completeness        | 30%     | All sections addressed                        |  
| Accuracy            | 40%     | Technical correctness                         |  
| Critical Analysis   | 20%     | Depth of ethical and practical insights      |  
| Clarity             | 10%     | Organization and presentation                 |  

---

## Part 1: Short Answer Questions (30 points)

### 1. Problem Definition (6 points)

**Hypothetical AI Problem:**  
*Predicting student dropout rates at universities.*

**Objectives:**  
1. Accurately identify students at high risk of dropping out early in their academic program.  
2. Provide actionable insights to university counselors to help intervene and support at-risk students.  
3. Improve overall student retention rates by enabling timely support and resource allocation.

**Stakeholders:**  
- University administration and academic counselors (need actionable data to reduce dropout).  
- Students (their academic success and well-being are directly impacted).

**Key Performance Indicator (KPI):**  
- **Dropout Prediction Accuracy** — The percentage of correctly predicted dropout cases versus actual dropouts, measured after each semester.

---

### 2. Data Collection & Preprocessing (8 points)

**Data Sources:**  
1. University records — including academic grades, attendance records, course enrollment data.  
2. Student surveys and socio-economic data — information on students’ backgrounds, financial status, mental health indicators.

**Potential Bias:**  
- The dataset might underrepresent students from marginalized groups who are less likely to participate in surveys or have incomplete records, causing the model to underperform for these students.

**Preprocessing Steps:**  
1. **Handling Missing Data:** Fill missing values using imputation methods such as mean substitution for grades or mode for categorical features like gender.  
2. **Normalization:** Scale numerical features like GPA and attendance percentages to a 0-1 range to help models converge faster.  
3. **Encoding Categorical Variables:** Convert categorical data such as course major or ethnicity into numerical form using one-hot encoding to be digestible by machine learning algorithms.

---

### 3. Model Development (8 points)

**Model Choice:**  
- **Random Forest Classifier** — chosen because it handles mixed data types well, is robust to noise, can model nonlinear relationships, and offers feature importance scores that help interpret the model.

**Data Splitting:**  
- Split the dataset into:  
  - **Training set (70%)** to train the model.  
  - **Validation set (15%)** to tune hyperparameters and prevent overfitting.  
  - **Test set (15%)** to evaluate final model performance on unseen data.

**Hyperparameters to Tune:**  
1. **Number of Trees (`n_estimators`):** Controls how many decision trees are built; too few can lead to underfitting, too many increase computation time.  
2. **Maximum Tree Depth (`max_depth`):** Limits how deep each tree grows; controls model complexity and helps prevent overfitting.

---

### 4. Evaluation & Deployment (8 points)

**Evaluation Metrics:**  
- **Accuracy:** Measures the overall proportion of correct predictions (dropout vs non-dropout). Useful for balanced datasets.  
- **F1-Score:** Harmonic mean of precision and recall; especially important when classes are imbalanced (e.g., fewer dropouts than non-dropouts).

**Concept Drift:**  
- *Definition:* Changes in the statistical properties of the input data over time, which can degrade model performance.  
- *Monitoring:* Track model accuracy over time on new student data; implement alerts if accuracy drops below a threshold, triggering retraining.

**Technical Challenge During Deployment:**  
- **Scalability:** The model should efficiently handle increasing student data across multiple departments/universities without excessive latency, requiring optimized code and possibly distributed computing.

---

## Part 2: Case Study Application (40 points)

**Scenario:**  
A hospital wants an AI system to predict patient readmission risk within 30 days of discharge.

---

### Problem Scope (5 points)

**Problem:**  
Predict which patients are at high risk of being readmitted within 30 days after discharge to enable preventive care and reduce hospital costs.

**Objectives:**  
1. Identify patients with high readmission risk early.  
2. Help medical staff prioritize follow-up care for these patients.  
3. Reduce avoidable readmissions and improve patient outcomes.

**Stakeholders:**  
- Hospital administration (aiming to reduce costs and improve care quality).  
- Medical professionals (doctors and nurses who use the model to plan patient care).

---

### Data Strategy (10 points)

**Data Sources:**  
- Electronic Health Records (EHRs) including diagnoses, treatments, medications.  
- Patient demographics (age, gender, socio-economic status).  
- Previous admission history and comorbidities.

**Ethical Concerns:**  
1. **Patient Privacy:** Strict safeguards must protect sensitive medical data.  
2. **Bias:** Historical data may underrepresent minority populations, risking biased predictions.

**Preprocessing Pipeline:**  
1. **Data Cleaning:** Remove duplicate records, correct errors in EHRs.  
2. **Feature Engineering:** Create features such as number of previous admissions, length of stay, and comorbidity index.  
3. **Normalization and Encoding:** Normalize numerical features and encode categorical variables (e.g., diagnosis codes) using one-hot encoding.

---

### Model Development (10 points)

**Model Selection:**  
- **Gradient Boosting Machines (e.g., XGBoost):** Chosen for high predictive accuracy and ability to handle heterogeneous data typical in healthcare.

**Confusion Matrix (Hypothetical):**

|                    | Predicted Readmit | Predicted No Readmit |  
|--------------------|-------------------|---------------------|  
| Actual Readmit     | 80                | 20                  |  
| Actual No Readmit  | 15                | 185                 |  

**Precision Calculation:**  
Precision = TP / (TP + FP) = 80 / (80 + 15) = 0.842 or 84.2%

**Recall Calculation:**  
Recall = TP / (TP + FN) = 80 / (80 + 20) = 0.80 or 80%

---

### Deployment (10 points)

**Integration Steps:**  
1. Develop an API endpoint to expose the model predictions to hospital software.  
2. Integrate with the hospital’s Electronic Health Record system to automatically fetch patient data and return risk scores.  
3. Provide an interface/dashboard for clinicians to view predictions and recommended actions.

**Healthcare Compliance:**  
- Ensure compliance with **HIPAA** by encrypting data at rest and in transit, enforcing role-based access controls, and maintaining audit logs.

---

### Optimization (5 points)

**Method to Address Overfitting:**  
- Implement **cross-validation** and early stopping during training. Use regularization parameters (e.g., L1/L2 penalties) in Gradient Boosting to prevent overfitting to training data.

---

## Part 3: Critical Thinking (20 points)

### Ethics & Bias (10 points)

**Effect of Biased Training Data:**  
- If certain patient groups (e.g., minorities or low-income) are underrepresented or misrepresented, the model may predict readmission risk less accurately for them, leading to unequal care and potentially worse health outcomes.

**Mitigation Strategy:**  
- Use fairness-aware techniques such as re-sampling underrepresented groups, or apply bias detection and mitigation tools like IBM AI Fairness 360 to identify and reduce bias.

---

### Trade-offs (10 points)

**Interpretability vs Accuracy:**  
- Highly accurate models (like ensemble methods) may be complex and hard to interpret, which is problematic in healthcare where decisions must be explainable to clinicians.  
- Simpler models (e.g., logistic regression) offer transparency but might sacrifice some accuracy.

**Impact of Limited Resources:**  
- Limited computational power favors simpler, less resource-intensive models which may reduce prediction accuracy but improve deployment feasibility and responsiveness in hospital settings.

---

## Part 4: Reflection & Workflow Diagram (10 points)

### Reflection (5 points)

**Most Challenging Part:**  
- Balancing model accuracy with ethical fairness and interpretability was the toughest, as improving one often impacts the others. Ensuring compliance with healthcare regulations also posed significant challenges.

**Improvements with More Resources:**  
- Gathering more diverse data to reduce bias, investing in explainable AI tools, and building a robust monitoring system for model drift would greatly enhance the project.

---

### Workflow Diagram (5 points)

(Sketch and include a flowchart of the AI Development Workflow stages below:)

```text
+------------------+
| Problem Definition|
+------------------+
          |
          v
+------------------+
| Data Collection & |
|   Preprocessing  |
+------------------+
          |
          v
+------------------+
| Model Development|
+------------------+
          |
          v
+------------------+
| Evaluation &     |
| Deployment       |
+------------------+
          |
          v
+------------------+
| Monitoring &     |
| Maintenance      |
+------------------+
References
IBM AI Fairness 360 Toolkit: https://aif360.mybluemix.net/

HIPAA Compliance Guidelines: https://www.hhs.gov/hipaa/index.html

CRISP-DM Framework: https://www.datascience-pm.com/crisp-dm-2/

XGBoost Documentation: https://xgboost.readthedocs.io/en/latest/

Author
Kgololosego Moleba
kgolomoleba@gmail.com
