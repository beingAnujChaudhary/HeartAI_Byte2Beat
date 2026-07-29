# HeartAI_Byte2Beat

**Explainable AI for Cardiovascular Disease Risk Prediction Using Clinical Feature Engineering and SHAP Analysis**

An official submission for the **Hack4Health: Byte 2 Beat Hackathon**. 

## 📌 Project Overview
Cardiovascular disease (CVD) remains a highly complex health challenge. While machine learning offers powerful predictive capabilities, black-box AI models face low clinical adoption due to a lack of transparency. 

This project evaluates 70,000 patient records to develop an **explainable machine learning framework**. By engineering physiologically grounded clinical features and utilizing gradient boosting (XGBoost) combined with SHAP (SHapley Additive exPlanations), we achieve a highly predictive and fully interpretable CVD risk model.

## ✨ Key Features
*   **Clinical Data Sanity Checks:** Rigorous EDA filtering to remove physiologically impossible blood pressure readings (e.g., 16,020 mmHg), protecting the model from data-entry artifacts.
*   **Clinical Feature Engineering:** Transformation of raw data into doctor-friendly metrics, including **BMI**, **Pulse Pressure**, and **Mean Arterial Pressure (MAP)**.
*   **Feature Ablation Study:** Mathematical validation proving that the inclusion of our engineered clinical features measurably improves the ROC-AUC score.
*   **Probability Calibration:** A reliability diagram confirming the model's predicted probabilities align with actual observed incidences, a critical step for real-world clinical deployment.
*   **SHAP Explainability:** Transparent breakdown of the model's reasoning, revealing that our engineered `MAP` and `BMI` rank among the top 5 most critical predictors.
*   **Interactive Coder Infrastructure:** Dynamic, infrastructure-as-code deployment allowing users to customize compute resources and SHAP visualization limits prior to provisioning.

## 📊 Results
After 20 trials of Optuna hyperparameter optimization, the finalized XGBoost model achieved:
*   **Test AUC:** 0.8053
*   **Accuracy:** ~74%
*   **F1-Score:** ~0.73

## 📂 Repository Structure
As per the hackathon reproducibility guidelines, the repository is structured as follows:

```text
HeartAI_Byte2Beat/
├── data/                  # Directory for the processed dataset
├── figures/               # Saved performance plots (ROC, Calibration, SHAP, Ablation)
├── models/                # Exported XGBoost model weights (.json)
├── notebooks/             # Main Jupyter Notebook containing the full pipeline
├── .gitignore             # Git ignore file
├── LICENSE                # MIT License
├── README.md              # Project documentation
├── main.tf                # Coder Terraform template for interactive workspaces
└── requirements.txt       # Python dependencies for full reproducibility

```

## 🚀 How to Run (Coder Integration)

To ensure full reproducibility and to qualify for the Coder integration track, this project is configured to run inside an interactive Coder workspace.

1. **Initialize Coder:** Import the `main.tf` Terraform template into your Coder deployment.


2. **Customize Workspace:** The interactive UI will prompt you to select your compute tier and specify the `SHAP_DISPLAY_COUNT` (how many top clinical features the SHAP summary plot should render).


3. **Clone & Install:** Inside the Coder terminal, clone this repository and install the dependencies:
```bash
git clone [https://github.com/beingAnujChaudhary/HeartAI_Byte2Beat.git](https://github.com/beingAnujChaudhary/HeartAI_Byte2Beat.git)
cd HeartAI_Byte2Beat
pip install -r requirements.txt

```


4. **Run the Notebook:** Launch the Jupyter Notebook in `notebooks/`. The code will automatically detect the Coder environment variables and adjust the SHAP explainability outputs dynamically based on your workspace configuration.

## ⚠️ Limitations & Future Work

* **Reporting Bias:** Lifestyle factors (alcohol and smoking) demonstrated surprisingly low predictive power, likely pointing to patient under-reporting bias in the dataset.
* **Cross-Sectional Data:** The current dataset prevents true longitudinal disease forecasting.
* **Future Directions:** Incorporating Decision Curve Analysis (Net Benefit) and evaluating the performance of these engineered features on continuous, time-series physiological data.

## 🤖 Generative AI Disclosure

Generative AI was utilized strictly as a coding assistant for standard Python/Matplotlib syntax and Optuna debugging. All clinical hypotheses, feature engineering decisions, data sanity checks, and written reports were generated entirely by the human team.
