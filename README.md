<div align="center">

<!-- BANNER -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=200&section=header&text=Telco%20Customer%20Churn%20Analysis&fontSize=40&fontColor=fff&animation=fadeIn&fontAlignY=38&desc=Predicting%20Customer%20Departure%20Before%20It%20Happens&descAlignY=55&descAlign=50" width="100%"/>

<!-- BADGES -->
<p>
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/Status-Completed-2ecc71?style=for-the-badge"/>
</p>

<p>
  <img src="https://img.shields.io/badge/Customers%20Analyzed-7%2C043-blueviolet?style=flat-square"/>
  <img src="https://img.shields.io/badge/Features%20Engineered-33%2B-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Models%20Built-2-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/Churn%20Rate%20Found-26.5%25-red?style=flat-square"/>
</p>

</div>

---

## 📌 Table of Contents

- [The Business Problem](#-the-business-problem)
- [Project Objective](#-project-objective)
- [Dataset Overview](#-dataset-overview)
- [Project Workflow](#-project-workflow)
- [Key Insights & Findings](#-key-insights--findings)
- [Feature Engineering](#-feature-engineering)
- [Model Performance](#-model-performance)
- [Business Recommendations](#-business-recommendations)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [What I Learned](#-what-i-learned)

---

## 💼 The Business Problem

> *"It costs **5× more** to acquire a new customer than to retain an existing one."*
> — Harvard Business Review

A mid-sized telecom company was silently hemorrhaging customers every single month. Contracts were ending. Calls were dropping. Competitors were circling. Yet the business had **no system** to identify which customers were on the verge of leaving — until it was too late.

**The question posed to data:**
> *"Can we predict which customers are about to churn — and act before they do?"*

This project is the answer.

---

## 🎯 Project Objective

| Goal | Description |
|------|-------------|
| 🔍 **Diagnose** | Understand *why* customers are churning through deep exploratory analysis |
| 📊 **Quantify** | Measure churn across every customer segment with statistical precision |
| 🤖 **Predict** | Build machine learning models that flag at-risk customers before they leave |
| 💡 **Recommend** | Translate data findings into concrete business actions the company can execute |

---

## 📦 Dataset Overview

| Property | Detail |
|----------|--------|
| **Source** | IBM Telco Customer Churn Dataset |
| **Rows** | 7,043 customer records |
| **Columns** | 33 features |
| **Target Variable** | `Churn` (Binary: 0 = Retained, 1 = Churned) |
| **Domain** | Telecommunications |

### Feature Categories
```
📋 Demographics     →  Gender, Senior Citizen, Partner, Dependents
📱 Services         →  Phone, Internet, Online Security, Streaming TV/Movies
💳 Account Info     →  Contract Type, Payment Method, Paperless Billing
💰 Financials       →  Monthly Charges, Total Charges, Tenure
🎯 Target           →  Churn (Yes / No)
```

---

## 🔄 Project Workflow

```
Raw CSV Data
     │
     ▼
┌─────────────────┐
│  Data Cleaning   │  → Fix data types, handle nulls, drop irrelevant columns
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│      EDA         │  → 6 visualizations, pattern discovery, segment analysis
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│Feature Engineer. │  → 3 new features created to improve model signal
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Model Building   │  → Logistic Regression + Decision Tree
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Evaluation      │  → Accuracy, ROC-AUC, Confusion Matrix, Classification Report
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Recommendations  │  → 5 actionable business strategies derived from data
└─────────────────┘
```

---

## 🔍 Key Insights & Findings

### 1. Overall Churn Rate
> **26.5% of customers churned** — meaning roughly 1 in every 4 customers left the company. This is a critical business signal demanding immediate action.

---

### 2. Contract Type is the Strongest Churn Predictor

| Contract Type | Churn Rate |
|---------------|-----------|
| Month-to-Month | **~42%** 🔴 |
| One Year | ~11% 🟡 |
| Two Year | ~3% 🟢 |

**Insight:** Customers on month-to-month contracts churn at **14× the rate** of two-year contract holders. The lack of commitment creates zero switching cost.

---

### 3. The Dangerous First 12 Months

> Customers who have been with the company for less than 12 months represent the **highest churn concentration**. New customers haven't yet built loyalty — they're still evaluating the service.

---

### 4. High Charges Drive Departure

> Churned customers paid **significantly higher monthly charges** on average compared to retained customers. Combined with short tenure, this creates a "high cost, low loyalty" trap.

---

### 5. Fiber Optic Users Churn More Than DSL Users

> Despite being a premium service, Fiber Optic users showed **higher churn rates** than DSL users — suggesting unmet quality expectations or aggressive competitor pricing in the fiber segment.

---

### 6. Add-On Services Act as Retention Anchors

> Customers subscribed to services like **Online Security, Tech Support, and Device Protection** churned significantly less. Each additional service creates a deeper relationship with the platform.

---

## ⚙️ Feature Engineering

Three new features were created to give the model richer signals:

| New Feature | Formula | Business Logic |
|-------------|---------|----------------|
| `Avg_Monthly_Spend` | Total Charges ÷ Tenure Months | Identifies if spending increased over time |
| `Tenure_Bucket` | Binned into 4 groups | New / Growing / Established / Loyal |
| `Num_Services` | Count of Yes across 6 service columns | Measures how embedded the customer is |

> 💡 **Why this matters:** Raw features tell you *what happened*. Engineered features tell you *what it means*.

---

## 🤖 Model Performance

### Models Trained
- **Logistic Regression** — chosen for interpretability and business explainability
- **Decision Tree (max_depth=5)** — chosen for visual decision rules and feature importance

### Results

| Model | Accuracy | ROC-AUC Score |
|-------|----------|---------------|
| Logistic Regression | ~80% | ~0.84 |
| Decision Tree | ~79% | ~0.82 |

### Why Two Models?

> A single model is a guess. Two models with similar results is **evidence**. Both models independently agreed on the same top churn predictors — which means the findings are robust, not coincidental.

### Top 5 Churn Predictors (Decision Tree Feature Importance)

```
1. Tenure Months          ████████████████████  (Most Important)
2. Monthly Charges        ████████████████
3. Total Charges          ██████████████
4. Contract Type          ████████████
5. Num_Services           ██████████
```

---

## 💡 Business Recommendations

Based on the data analysis and model findings, here are **5 actionable strategies**:

### 🎯 Recommendation 1 — The 90-Day Loyalty Offer
> Target month-to-month customers at the **3-month mark** with a personalized offer to switch to an annual contract at a 15–20% discount. This is the highest-leverage intervention point.

### 🚀 Recommendation 2 — Build a New Customer Onboarding Program
> The first 12 months are the most dangerous. Create a structured onboarding journey — welcome calls, usage tips, check-ins at day 30/60/90 — to build early loyalty before competitors can poach.

### 📦 Recommendation 3 — Bundle Add-On Services Strategically
> Customers with 3+ services churn significantly less. Offer **free 3-month trials** of Online Security or Tech Support to customers with 0–1 services. Once adopted, they rarely leave.

### 📞 Recommendation 4 — Proactive Outreach for High-Risk Fiber Users
> Identify Fiber Optic customers in months 4–8 with high monthly charges and no add-ons. Assign them to a retention specialist before they start shopping competitors.

### 🤖 Recommendation 5 — Deploy a Monthly Churn Scoring System
> Run this model on the full customer base every month. Flag the **top 20% highest churn-risk customers** for proactive retention outreach. Prevention is always cheaper than win-back.

---

## 🛠 Tech Stack

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Seaborn-4c72b0?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white"/>
</p>

---

## 📁 Project Structure

```
📦 Telco-Customer-Churn-Analysis
 ┣ 📓 Telco_Churn_Analysis.ipynb   ← Main analysis notebook (6 sections)
 ┣ 📊 Telco_customer_churn.csv     ← Raw dataset (7,043 rows)
 ┗ 📄 README.md                    ← You are here
```

---

## ▶️ How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Steps
```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/Telco-Customer-Churn-Analysis.git

# 2. Navigate into the folder
cd Telco-Customer-Churn-Analysis

# 3. Launch Jupyter Notebook
jupyter notebook

# 4. Open Telco_Churn_Analysis.ipynb and Run All Cells
```

> ⚠️ Make sure `Telco_customer_churn.csv` is in the **same folder** as the notebook before running.

---

## 📚 What I Learned

| Skill | What Was Practiced |
|-------|--------------------|
| **Data Cleaning** | Handling mixed data types, null imputation, dropping irrelevant features |
| **EDA** | Asking business-driven questions and answering them visually |
| **Feature Engineering** | Creating new variables that encode domain knowledge |
| **Machine Learning** | Training, evaluating, and comparing classification models |
| **Business Thinking** | Translating statistical findings into executive-level recommendations |
| **Storytelling** | Structuring a data project as a narrative, not just a code dump |

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer"/>

**⭐ If this project helped you, please give it a star — it keeps me motivated to build more!**

*Built with curiosity, Python, and a lot of ☕*

</div>
