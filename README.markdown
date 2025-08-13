# Health Insurance Cost Predictor ML Project for Shield Insurance

## Description
This project develops a predictive model for Shield Insurance to estimate health insurance premiums based on factors such as age, smoking habits, BMI, medical history, and genetic risk. Built using Python, it employs Linear Regression models segmented by age (young: ≤25 years, rest: >25 years) to achieve >97% accuracy, with only 0.3% of predictions having errors >10%, meeting the requirement that 95% of errors are <10%. A Streamlit-based application enables insurance underwriters to input client data and receive real-time premium predictions. The project fulfills Phase 1 (MVP) requirements of the Statement of Work (SOW) with AtliQ AI.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Features](#features)
- [Model Details](#model-details)
- [Contributing](#contributing)
- [Contact](#contact)

## Installation
Follow these steps to set up the project locally:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/health-insurance-predictor.git
   ```
2. **Navigate to the Project Directory**:
   ```bash
   cd health-insurance-predictor
   ```
3. **Create a Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
4. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   Required packages:
   - joblib
   - pandas
   - numpy
   - scikit-learn
   - xgboost
   - streamlit
   - matplotlib
   - seaborn

5. **Ensure Dataset Availability**:
   Place the dataset (`premiums_with_gr.xlsx`) in the `data/` folder. Segmented datasets (`premiums_young_with_gr.xlsx`, `premiums_rest_with_gr.xlsx`) are generated via `Healthcare Prediction data segmentation.ipynb`.

## Usage
To explore the model development or run the Streamlit application:

1. **Model Development**:
   - Open `Healthcare Premium Prediction.ipynb` in Jupyter Notebook to review initial analysis and error identification.
   - Run `Healthcare Prediction data segmentation.ipynb` to split the dataset into young (≤25 years) and rest (>25 years) groups.
   - Use `Healthcare Premium Prediction Young with GR.ipynb` and `Healthcare Premium Prediction Rest with GR.ipynb` to train and save models for the young and rest age groups, respectively.
   - Models and scalers are saved to `artifacts/` as `model_young.joblib`, `model_rest.joblib`, `scaler_young.joblib`, and `scaler_rest.joblib`.

2. **Run the Streamlit App**:
   ```bash
   streamlit run Main.py
   ```
   - Open `http://localhost:8501` in your browser.
   - Input client details (e.g., age, BMI category, smoking status, medical history, etc.).
   - Click "Predict" to view the estimated health insurance premium.

### Example
```python
# Example input in Streamlit app
Age: 30
Number of Dependants: 2
Income in Lakhs: 10
Genetical Risk: 3
Insurance Plan: Silver
Employment Status: Salaried
Gender: Female
Marital Status: Married
BMI Category: Normal
Smoking Status: No Smoking
Region: Northwest
Medical History: Diabetes
```

Output:
- Predicted Health Insurance Cost: e.g., 15000

## Project Structure
```
health-insurance-predictor/
├── artifacts/                                   # Saved models and scalers
│   ├── model_young.joblib
│   ├── model_rest.joblib
│   ├── scaler_young.joblib
│   ├── scaler_rest.joblib
├── data/                                       # Input datasets
│   ├── premiums_with_gr.xlsx
│   ├── premiums_young_with_gr.xlsx
│   ├── premiums_rest_with_gr.xlsx
├── Healthcare Premium Prediction.ipynb         # Initial analysis and error identification
├── Healthcare Prediction data segmentation.ipynb  # Data segmentation by age
├── Healthcare Premium Prediction Young.ipynb   # Model for young without genetic risk
├── Healthcare Premium Prediction Rest.ipynb    # Model for rest without genetic risk
├── Healthcare Premium Prediction Young with GR.ipynb  # Model for young with genetic risk
├── Healthcare Premium Prediction Rest with GR.ipynb   # Model for rest with genetic risk
├── Main.py                                    # Streamlit app for predictions
├── Predictor_Helper.py                        # Helper functions for prediction
├── requirements.txt                           # Project dependencies
└── README.md                                  # Project documentation
```

## Features
- **Data Preprocessing**: Segments dataset (50,000 records) into young (20,096 rows, ≤25 years) and rest (29,904 rows, >25 years) to address error patterns.
- **Feature Engineering**: Includes numerical features (`age`, `number_of_dependants`, `income_lakhs`, `genetical_risk`, `normalized_risk_score`) and one-hot encoded categoricals (`Gender`, `Region`, `Marital Status`, `BMI Category`, `Smoking Status`, `Employment Status`).
- **Model**: Linear Regression models (with Ridge/Lasso experimentation) optimized via GridSearchCV/RandomizedSearchCV.
- **Streamlit UI**: Interactive interface for underwriters to input client data and view premium predictions.
- **Metrics**: Achieves >97% accuracy, with only 0.3% of predictions having >10% error, meeting SOW requirements.
- **Scalability**: Models are saved for potential cloud deployment (not implemented in provided files).

## Model Details
- **Algorithm**: Linear Regression (with Ridge/Lasso evaluated).
- **Segmentation**: Two models:
  - Young (≤25 years): Trained on `premiums_young_with_gr.xlsx`.
  - Rest (>25 years): Trained on `premiums_rest_with_gr.xlsx`.
- **Features Used**:
  - Numerical: `age`, `number_of_dependants`, `income_lakhs`, `genetical_risk`, `normalized_risk_score` (derived from medical history).
  - Categorical (one-hot encoded): `gender_Male`, `region_Northwest`, `region_Southeast`, `region_Southwest`, `marital_status_Unmarried`, `bmi_category_Obesity`, `bmi_category_Overweight`, `bmi_category_Underweight`, `smoking_status_Occasional`, `smoking_status_Regular`, `employment_status_Salaried`, `employment_status_Self-Employed`, `insurance_plan` (encoded as 1–3).
- **Output**: Predicted annual premium (integer).
- **Model Storage**: Saved as `model_young.joblib` and `model_rest.joblib`, with scalers in `scaler_young.joblib` and `scaler_rest.joblib`.
- **Performance**: Both models achieve 0.3% extreme errors (>10%), ensuring 95% of predictions have <10% error, with >97% accuracy.

## Contributing
Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add your feature description"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/your-feature-name
   ```
5. Open a pull request.

Please follow PEP 8 standards and include tests for new features.

## Contact
For questions or feedback, reach out to:
- Your Name: kavineshdhanush@gmail.com
