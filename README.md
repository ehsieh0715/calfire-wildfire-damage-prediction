# 🔥 California Wildfire Damage Prediction

Predicting wildfire-induced structural damage using data quality pipelines and interpretable machine learning.

**Binary Classification | Tabular Data | Imbalanced Dataset**

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-EDA-orange)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-yellow)
![Model](https://img.shields.io/badge/Model-Random%20Forest-brightgreen)
![Task](https://img.shields.io/badge/Task-Binary%20Classification-purple)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 🚀 Highlights
- Built an end-to-end ML pipeline (data → features → model → evaluation) for wildfire damage prediction
- Conducted exploratory data analysis (EDA) to identify key risk factors
- Reduced feature set from **151 → 45** while maintaining performance
- Final model: **Random Forest (F1 ≈ 0.891)**
- Focus on **real-world data quality, feature engineering, and model interpretability**

## 🌐 Quick Access
- 👉 [Data Quality Report (EDA Summary)](reports/Data%20Quality%20Report.pdf)
- 👉 [Data Quality Plan (Cleaning Strategy)](reports/Data%20Quality%20Plan.pdf)
- 👉 [View Data Preparation & EDA](notebooks/01_data_preparation.html)
- 👉 [View Modeling Results](notebooks/02_modeling_and_evaluation.html)

## 📌 Overview

This project analyzes wildfire damage data from the California Department of Forestry and Fire Protection (CAL FIRE) and builds a structured pipeline to predict structure damage severity under wildfire conditions.

The task is formulated as a binary classification problem, identifying whether a structure is "Destroyed (>50%)".

The analysis emphasizes data quality, feature engineering, and interpretable machine learning for real-world decision support.

## 📚 Table of Contents
- [Key Contributions](#-key-contributions)
- [Data Quality & EDA Outputs](#-data-quality--eda-outputs)
- [Modeling Results](#-modeling-results)
- [Skills Demonstrated](#-skills-demonstrated)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Future Work](#-future-work)

## 🚀 Key Contributions
- Built a **data quality assessment pipeline** for real-world data issues
- Designed and applied **data cleaning strategies** to improve reliability
- Conducted **EDA and statistical analysis** to guide feature engineering decisions
- Engineered **domain-informed features** for wildfire risk modeling
- Developed and evaluated **classification models**
- Produced **model-ready datasets**

## 📄 Data Quality & EDA Outputs

This project includes detailed data quality analysis and cleaning strategies:

-  [Data Quality Report](reports/Data%20Quality%20Report.pdf): identifies key issues such as missing values, high cardinality, inconsistent formatting, and long-tail distributions  
-  [Data Quality Plan](reports/Data%20Quality%20Plan.pdf): documents feature-level decisions for cleaning, imputation, and transformation  

These reports capture the reasoning behind data preprocessing and feature engineering decisions, ensuring transparency and reproducibility.

### 🔍 EDA Insights

EDA reveals several factors associated with severe fire damage:

- **Structure Type:**  
  Mobile homes exhibit significantly higher destruction rates (>70%), likely due to lightweight materials and lower structural stability.

- **Roof Construction:**  
  Both combustible and fire-resistant materials are associated with high damage rates, suggesting potential heat retention and smoldering effects.

- **Exterior Siding:**  
  Multiple siding types exhibit similarly high damage rates (~90%), indicating complex interactions between fire spread and heat retention.

- **Ventilation Systems:**  
  Buildings with vents exhibit higher damage rates, likely due to ember intrusion and increased oxygen supply.


## 🤖 Modeling Results

### 📊 Model Comparison (Test Set)

| Model               | Accuracy | Precision | Recall | F1-score | AUC |
|---------------------|----------|-----------|--------|----------|-----|
| Baseline (Always 1) | 0.579    | 0.579     | 1.000  | 0.733    | —   |
| Linear Regression   | 0.819    | 0.855     | 0.826  | 0.840    | —   |
| Logistic Regression | 0.822    | 0.894     | 0.785  | 0.836    | 0.91|
| Random Forest       | 0.836    | 0.861     | 0.853  | 0.857    | 0.92|

All results are evaluated on a held-out test set, where Random Forest achieves the best balance across precision, recall, and F1-score and is selected for further optimization.

### 🏆 Final Model & Optimization

We further optimized Random Forest through feature selection:

- Full model: **151 features → F1 ≈ 0.893**
- Reduced model: **45 features → F1 ≈ 0.891**

The final model is **Random Forest (v4-2, 45 features)**:
- Reduces feature count by ~70%
- Maintains nearly identical performance
- Improves efficiency and interpretability

This demonstrates that feature selection enables significant model simplification without sacrificing predictive performance, making the model more suitable for real-world deployment.

### 🔎 Reconciling EDA and Model Findings

EDA highlights associations between individual features and damage severity, while model-based interpretations capture conditional effects and feature interactions.

For example, structure types such as mobile homes show high risk in EDA but lower importance in the Random Forest model, as they do not frequently co-occur with other predictive features. In contrast, temporal features (e.g., incident year and month) receive higher importance due to their interaction effects across the dataset.

These differences emphasize the importance of combining exploratory analysis with model-based interpretation to understand both observable patterns and predictive structure, improving the reliability of real-world insights.

## 🧠 Skills Demonstrated
- Data Cleaning & Validation
- Exploratory Data Analysis (EDA)
- Feature Engineering & Selection
- Machine Learning (Classification Models)
- Reproducibility & Pipeline Design

## 📁 Project Structure 
The project follows a standard data science workflow:

```
calfire-wildfire-damage-prediction/
│
├── data/
│   ├── raw/                  # Original datasets
│   │   ├── cal-wildfires-23224143.csv
│   │   └── CAL FIRE Administrative Units.csv
│   │
│   ├── interim/              # Intermediate data
│   │   └── fixed_address.csv
│   │
│   └── processed/            # Cleaned datasets
│       ├── cal_wildfires_cleaned.csv
│       ├── cal_wildfires_standardized.csv
│       └── cal_wildfire_final_features.csv
│
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 01_data_preparation.html        # Full data quality analysis
│   ├── 02_modeling_and_evaluation.ipynb
│   └── 02_modeling_and_evaluation.html # Full modeling & evaluation
│
├── reports/
│   ├── Data Quality Report.pdf         
│   └── Data Quality Plan.pdf           
│
├── requirements.txt                   # Python dependencies
├── .gitignore
└── README.md
```

## ▶️ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/ehsieh0715/calfire-wildfire-damage-prediction.git
cd calfire-wildfire-damage-prediction
```
### 2. Create virtual environment (recommended)
```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```
### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run analysis

You can explore the project in two ways:
- Open HTML notebooks (recommended for viewing results):
    - notebooks/01_data_preparation.html
	- notebooks/02_modeling_and_evaluation.html
- Or run Jupyter notebooks:
```bash
jupyter lab
```

## 🔮 Future Work
- Explore advanced models (XGBoost, LightGBM)
- Improve spatial features (GIS-based analysis)
- Address class imbalance more systematically