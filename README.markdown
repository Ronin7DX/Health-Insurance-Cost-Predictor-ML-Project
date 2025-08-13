# Predictive Health Insurance Model for Shield Insurance

## Description
This project develops a predictive model for Shield Insurance to estimate health insurance premiums based on factors such as age, smoking habits, BMI, medical history, and genetic risk. Built using Python, it employs Linear Regression models segmented by age (young: ≤25 years, rest: >25 years) to achieve >97% accuracy, with only 0.3% of predictions having errors >10%, meeting the requirement that 95% of errors are <10%. A Streamlit-based application enables insurance underwriters to input client data and receive real-time premium predictions. The project fulfills Phase 1 (MVP) requirements of the Statement of Work (SOW) with AtliQ AI.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Features](#features)
- [Model Details](#model-details)
- [Contributing](#contributing)
- [License](#license)
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
To explore the model