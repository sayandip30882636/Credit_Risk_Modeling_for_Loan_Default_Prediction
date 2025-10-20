
# 💳 Credit Risk Modeling for Loan Default Prediction (Basel III Framework)

### 📘 Overview
This project builds a **machine learning–driven Credit Risk Modeling pipeline** to estimate:
- **Probability of Default (PD)**  
- **Loss Given Default (LGD)**  
- **Exposure at Default (EAD)**  
and computes **Expected Loss (EL)** and **Risk-Weighted Assets (RWA)** under **Basel III** regulatory standards.

Using historical retail loan data (simulated LendingClub dataset), the pipeline estimates borrower-level default probabilities, quantifies expected losses, and visualizes portfolio-level risk exposures.

---

## 🧠 Objectives
- Predict **loan default probability (PD)** using advanced ML models (LightGBM, Logistic Regression).  
- Estimate **LGD** and **EAD** for credit exposure simulation.  
- Compute **Expected Loss (EL = PD × LGD × EAD)**.  
- Derive **Basel III Risk-Weighted Assets (RWA)**.  
- Provide interpretable **risk dashboards and business insights**.

---

## 🏗️ Project Architecture
The project is divided into structured phases:

| Phase | Description | Key Output |
|:------|:-------------|:------------|
| **A. Data Loading & EDA** | Load dataset, perform EDA, handle missing data, engineer new features | Cleaned dataset & preprocessing pipeline |
| **B. Model Development** | Train Logistic Regression & LightGBM; tune hyperparameters | Calibrated PD models (AUC ≈ 0.84) |
| **C. Risk Parameter Estimation** | Simulate LGD & EAD; compute EL and RWA using Basel III IRB formula | `phaseC_risk_estimates.csv` |
| **D. Visualization & Portfolio Analysis** | Visualize PD, LGD, EAD, EL distributions & correlations | Interactive risk charts |
| **E. Results & Interpretation** | Summarize metrics, feature importance, and segment-level insights | Final summary & CV-ready results |

---

## 📊 Key Results

| Metric | Value (approx.) | Interpretation |
|:-------|:----------------|:----------------|
| **AUC (LightGBM)** | 0.84 | Excellent discrimination between good and bad loans |
| **Mean PD** | ~3–4% | Avg probability of default per borrower |
| **Mean LGD** | ~0.55 | Avg proportion lost when a borrower defaults |
| **Total Expected Loss** | Portfolio-level sum | Overall expected credit loss |
| **Top Risk Drivers** | Interest Rate, DTI, Loan-to-Income, Credit Stress | Strongest predictors of default |

**Business Insight:**  
Loans with higher interest rates, high DTI, and small business purposes show significantly elevated risk levels and should be monitored more closely.

---

## 🧩 Visual Outputs
- 📈 PD, LGD, EAD Distribution plots  
- 🔥 Feature importance (LightGBM Gain)  
- 🧮 Expected Loss histogram  
- 🧾 Risk segmentation by loan purpose  
- 🧠 Correlation heatmap (PD, LGD, EAD, EL, RWA)

---

## ⚙️ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/credit-risk-modeling.git
cd credit-risk-modeling
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the pipeline step-by-step
Each notebook or script corresponds to a phase:
```bash
python phaseA_preprocessing.py
python phaseB_modeling.py
python phaseC_risk_estimation.py
python phaseD_visualization.py
python phaseE_summary.py
```

### 4. Outputs
All processed data, models, and visual results are saved under:
```
/data/
 ├── pd_preprocessor.pkl
 ├── pd_lgb_phaseB.pkl
 ├── phaseC_risk_estimates.csv
 ├── final_portfolio_summary.csv
```

---

## 🧰 Technologies Used
- **Python 3.12+**
- **Pandas, NumPy** – data handling  
- **Scikit-learn** – preprocessing, modeling, calibration  
- **LightGBM** – gradient boosting for PD modeling  
- **Matplotlib / Seaborn** – visualization  
- **Joblib / Pickle** – model persistence  

---

## 📁 Repository Structure
```
credit-risk-modeling/
│
├── data/                     # Input & output data files
├── notebooks/                # Jupyter notebooks for each phase
├── scripts/                  # Python scripts (A–E)
├── README.md                 # Project overview
├── requirements.txt          # Dependencies
└── LICENSE
```

---

## 📘 Interpretations (Business Context)
- A **PD of 3–4%** suggests the portfolio is low-to-moderate risk overall.  
- **Higher PD** loans typically correspond to **higher interest rates or smaller income ratios**.  
- **Expected Loss (EL)** helps determine **loan loss provisions** under IFRS 9 / Basel III.  
- **RWA** translates these risks into **capital requirements**, influencing a bank’s capital adequacy ratio.

---

## 🧾 Example CV Description
> Developed a full-scale Credit Risk Modeling pipeline to estimate PD, LGD, EAD, and Basel III capital charges using LendingClub data (≈396k records).  
> Implemented LightGBM and logistic regression models, achieving AUC = 0.84.  
> Generated portfolio-level Expected Loss (EL) and RWA estimates, visualized risk drivers, and automated calibration.  

---

## 🧑‍💻 Author
**Sayandip Ghosh**  
📧 [sayandip3088@gmai.com]  
⭐ *If you found this helpful, please star the repo!*

---

## 🪙 License
This project is released under the **MIT License**.
````

---

Would you like me to also generate a **`requirements.txt`** file for this project (listing the exact Python dependencies)? It’ll make your GitHub repository plug-and-play for others.
