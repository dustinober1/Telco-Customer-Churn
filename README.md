# Telco Customer Churn Prediction

A comprehensive machine learning project for predicting customer churn in the telecommunications industry. This end-to-end solution includes data cleaning, exploratory data analysis, advanced feature engineering, multiple ML models, and business insights.

## 🎯 Project Overview

Customer churn is a critical business metric for telecom companies. This project predicts which customers are likely to cancel their services, enabling proactive retention strategies. The solution achieved **63.1% F1-Score** and **84.8% ROC AUC** using Random Forest with engineered features.

## 📊 Key Results

- **Best Model**: Random Forest Classifier
- **F1-Score**: 0.631 (robust for imbalanced data)
- **ROC AUC**: 0.848 (excellent discrimination)
- **Accuracy**: 75.8%
- **Recall**: 78% (captures most churning customers)
- **Precision**: 53% (reasonable false positive rate)

### Business Impact
- **26.6% baseline churn rate** in the dataset
- Model identifies **78% of churning customers** for proactive retention
- **Top churn drivers**: Contract type, tenure, monthly charges, and service complexity

## 📁 Project Structure

```
Telco-Customer-Churn/
├── data/                               # Data files
│   ├── WA_Fn-UseC_-Telco-Customer-Churn.csv  # Raw dataset (7043 customers)
│   ├── cleaned_telco_churn.csv         # Cleaned dataset (7032 customers)
│   └── featured_telco_churn.csv        # Feature-engineered dataset (71 features)
├── notebooks/                          # Jupyter notebooks
│   ├── 01-data-cleaning.ipynb         # Data preprocessing and cleaning
│   ├── 02-eda.ipynb                   # Exploratory data analysis
│   ├── 03-feature-engineering.ipynb   # Advanced feature creation
│   ├── 04-modeling.ipynb              # ML model training and evaluation
│   └── 05-interpretation.ipynb        # Model interpretation with SHAP
├── models/                             # Saved models and artifacts
│   ├── best_churn_model_random_forest.joblib
│   ├── feature_names.joblib
│   └── model_metadata.joblib
├── outputs/                            # Generated outputs
│   └── figures/                        # EDA visualizations
├── requirements.txt                    # Python dependencies
├── README.md                          # Project documentation
└── Executive_Summary.md               # Business summary
```

## 🚀 Quick Start

### Prerequisites
- Python 3.11+
- Jupyter Notebook or JupyterLab

### Installation
```bash
# Clone the repository
git clone https://github.com/dustinober1/Telco-Customer-Churn.git
cd Telco-Customer-Churn

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Running the Analysis
Execute notebooks in order:
1. **Data Cleaning**: `01-data-cleaning.ipynb`
2. **Exploratory Analysis**: `02-eda.ipynb`
3. **Feature Engineering**: `03-feature-engineering.ipynb`
4. **Modeling**: `04-modeling.ipynb`
5. **Interpretation**: `05-interpretation.ipynb`

## 📈 Data Pipeline

### Step 1: Data Cleaning
- **Input**: Raw CSV (7043 customers, 21 features)
- **Process**: Handle missing values, fix data types, one-hot encoding
- **Output**: Clean dataset (7032 customers, 47 features)
- **Key Issues Fixed**: TotalCharges formatting, 11 missing values removed

### Step 2: Exploratory Data Analysis
- **Churn Distribution**: 26.6% churn rate (1869 churned, 5163 retained)
- **Contract Analysis**: Month-to-month customers churn at 42.7% vs 2.8% for two-year contracts
- **Service Analysis**: Fiber optic internet and electronic check payments show higher churn
- **Generated**: Distribution plots, correlation matrices, churn rate analyses

### Step 3: Feature Engineering (24 New Features)
- **Tenure Features**: `tenure_in_years`, `tenure_group` (New/Medium/Long)
- **Ratio Features**: `monthly_charges_to_tenure_ratio`, `charges_vs_avg_ratio`
- **Binary Flags**: `has_dependents`, `has_premium_services`, `has_internet_service`
- **Risk Scores**: `payment_risk_score` (0-5 scale), `high_risk_combination`
- **Customer Segments**: Value-based segmentation (High/Low Value × New/Loyal)
- **Interaction Features**: Contract-charges and service-charges interactions

### Step 4: Machine Learning Models

#### Models Evaluated
1. **Logistic Regression** (Baseline)
   - F1-Score: 0.599, ROC AUC: 0.836
   - Interpretable coefficients, fast training
   
2. **Random Forest** (Best Model)
   - F1-Score: **0.631**, ROC AUC: **0.835**
   - Handles feature interactions, robust to outliers
   
3. **XGBoost**
   - F1-Score: 0.616, ROC AUC: **0.840**
   - Strong gradient boosting, good feature importance

#### Model Selection Criteria
- **F1-Score prioritized** for imbalanced classification
- Cross-validation with stratified folds
- Class balancing with appropriate weights

## 🔍 Key Business Insights

### Top Churn Drivers (Random Forest Feature Importance)
1. **Contract Type**: Month-to-month contracts (highest risk)
2. **Monthly Charges to Tenure Ratio**: High charges for new customers
3. **Tenure**: Longer tenure = lower churn probability
4. **Internet Service**: Fiber optic customers show higher churn
5. **Tech Support**: Lack of tech support increases churn risk

### Customer Segments & Churn Rates
- **High Value New** (793 customers): Premium customers, short tenure
- **Low Value New** (2312 customers): Highest risk segment
- **High Value Loyal** (1883 customers): Retention focus
- **Low Value Loyal** (2044 customers): Stable, long-term base

### Retention Strategies
1. **Contract Incentives**: Promote longer-term contracts with discounts
2. **New Customer Care**: Enhanced support for first 12 months
3. **Service Quality**: Improve fiber optic service experience
4. **Payment Simplification**: Reduce electronic check dependency
5. **Tech Support**: Expand technical support offerings

## 🛠 Technical Implementation

### Machine Learning Stack
- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **ML Models**: Scikit-learn, XGBoost
- **Model Interpretation**: SHAP
- **Model Persistence**: Joblib

### Performance Optimization
- Reduced estimators (50 vs 100) for faster training on limited compute
- Stratified cross-validation for reliable evaluation
- Class balancing for imbalanced data handling
- Feature scaling for logistic regression

### Evaluation Metrics
- **F1-Score**: Harmonic mean of precision and recall (primary metric)
- **ROC AUC**: Area under ROC curve (discrimination ability)
- **Precision**: True positive rate (prediction accuracy)
- **Recall**: Sensitivity (churn detection rate)
- **Confusion Matrix**: Detailed prediction breakdown

## 📋 Model Deployment Ready

The trained model is saved and ready for deployment:
- **Model File**: `models/best_churn_model_random_forest.joblib`
- **Feature List**: `models/feature_names.joblib`
- **Metadata**: Performance metrics and training details
- **Input Format**: 72 engineered features per customer
- **Output**: Churn probability (0-1) and binary prediction

## 🔄 Future Enhancements

1. **Real-time Deployment**: Streamlit web application for interactive predictions
2. **Model Monitoring**: Performance tracking and drift detection
3. **Advanced Features**: Time-series features, customer journey analysis
4. **Deep Learning**: Neural networks for complex pattern recognition
5. **A/B Testing**: Retention strategy effectiveness measurement

## 📝 Data Dictionary

### Original Features (Cleaned)
- `SeniorCitizen`: Binary (0/1) for senior citizen status
- `tenure`: Customer tenure in months
- `MonthlyCharges`: Monthly service charges ($)
- `TotalCharges`: Total charges to date ($)
- `Contract_*`: One-hot encoded contract types
- `PaymentMethod_*`: One-hot encoded payment methods
- `InternetService_*`: One-hot encoded internet service types
- Additional service features (OnlineSecurity, TechSupport, etc.)

### Engineered Features
- `tenure_in_years`: Tenure converted to years
- `monthly_charges_to_tenure_ratio`: Charges per tenure month
- `payment_risk_score`: 0-5 risk score based on payment and contract
- `customer_segment`: Value-based customer categorization
- `total_services`: Count of additional services
- `has_premium_services`: Binary flag for any premium add-ons

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/new-feature`
3. Commit changes: `git commit -am 'Add new feature'`
4. Push branch: `git push origin feature/new-feature`
5. Submit Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Author

**Dustin Ober**
- GitHub: [@dustinober1](https://github.com/dustinober1)
- Project: [Telco Customer Churn Prediction](https://github.com/dustinober1/Telco-Customer-Churn)

## 🙏 Acknowledgments

- Dataset: IBM Watson Analytics Sample Data
- Inspiration: Kaggle Telco Customer Churn competitions
- Tools: Scikit-learn, XGBoost, SHAP, Jupyter ecosystem

---

**Last Updated**: September 2025
**Status**: Production Ready
**Model Version**: 1.0

Files:
- `notebooks/01-data-cleaning.ipynb` — initial cleaning and encoding, saves cleaned CSV to `data/cleaned_telco_churn.csv`
- `notebooks/01-data-cleaning.ipynb` — initial cleaning and encoding, saves cleaned CSV to `data/cleaned_telco_churn.csv`
- `notebooks/02-eda.ipynb` — exploratory data analysis: distributions, churn rates by group, and figures saved to `reports/figures/`
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` — original dataset (source: public dataset used widely)

How to run:
1. Create a virtual environment and install requirements (see `requirements.txt`).
2. From the workspace root run `jupyter lab` or open `notebooks/01-data-cleaning.ipynb` in VS Code and run cells.

Notes:
- The notebook expects the CSV at the repository root. If you move files, update the path in the notebook.

Results from running `notebooks/01-data-cleaning.ipynb` (executed):

- Initial dataset shape: 7043 rows × 21 columns
- `TotalCharges` was read as object, converted to numeric. There were 11 blank-like values (0.16%) that became NaN.
- Because the missing fraction was small (<=5%), those 11 rows were dropped. New shape after handling `TotalCharges`: 7032 rows × 21 columns
- After trimming and one-hot encoding of categorical variables, the final cleaned dataset shape is 7032 rows × 47 columns
- Cleaned CSV saved to `data/cleaned_telco_churn.csv`

Results from running `notebooks/02-eda.ipynb` (executed):

- Cleaned data loaded: 7032 rows × 47 columns
- Key numeric columns: SeniorCitizen, tenure, MonthlyCharges, TotalCharges
- Churn rate by contract (from EDA summary):
	- Month-to-month: ~42.7% (count 3875)
	- One year: ~11.3% (count 1472)
	- Two year: ~2.8% (count 1685)
- Figures and correlation heatmap saved to `reports/figures/` and a small table of churn rates saved to `reports/eda_summary.csv`