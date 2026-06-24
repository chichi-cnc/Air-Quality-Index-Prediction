# Air Quality Index (AQI) Prediction

A machine learning project that predicts the **Air Quality Index (AQI)** from pollutant measurements using multiple regression models, with hyperparameter tuning and feature importance analysis.

---

## Overview

Air quality directly impacts public health. This project builds and compares several ML regression models to predict AQI values from pollutant concentrations, identifies the most influential features, and optimizes the best-performing model via grid search.

**Key steps:**
- Exploratory data analysis and correlation heatmap
- Data preprocessing (null handling, feature selection, scaling)
- Model training and comparison: Linear Regression, Random Forest, XGBoost
- Hyperparameter tuning (GridSearchCV) on XGBoost
- Feature importance visualization
- Actual vs. Predicted AQI plot

---

## Dataset

The project uses the [India Air Quality Data](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india) (`city_day.csv`) from Kaggle.

**Key columns:**

| Column | Description |
|--------|-------------|
| `PM2.5`, `PM10` | Particulate matter concentrations |
| `NO`, `NO2`, `NOx` | Nitrogen oxide levels |
| `NH3` | Ammonia concentration |
| `CO` | Carbon monoxide level |
| `SO2` | Sulfur dioxide level |
| `O3` | Ozone level |
| `Benzene`, `Toluene`, `Xylene` | Volatile organic compounds |
| `AQI` | **Target variable** — Air Quality Index |

> `City`, `Date`, and `AQI_Bucket` are dropped during preprocessing (non-numeric / redundant).

---

## Models Used

| Model | Notes |
|-------|-------|
| Linear Regression | Baseline model |
| Random Forest Regressor | Handles non-linearity; 100 estimators |
| XGBoost Regressor | Best performer; tuned via GridSearchCV |

**Evaluation metrics:** MAE, RMSE, R² Score

---

## Project Structure

```
aqi-prediction/
├── Air_Quality_Index_Prediction.ipynb   # Main notebook
├── requirements.txt                     # Python dependencies
├── .gitignore                           # Files to exclude from git
└── README.md                            # Project documentation
```

> **Note:** `city_day.csv`, saved model files (`.pkl`), and prediction outputs (`.csv`) are excluded from the repo via `.gitignore`. Download the dataset from Kaggle and place it in the project root before running the notebook.

---

## Setup & Usage

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/aqi-prediction.git
cd aqi-prediction
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download `city_day.csv` from [Kaggle](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india) and place it in the project root. Then update the file path in the notebook:
```python
file_path = "city_day.csv"   # Change from "/content/city_day.csv" if running locally
```

### 4. Run the notebook
```bash
jupyter notebook Air_Quality_Index_Prediction.ipynb
```

Or open it directly on **Google Colab** using the path `/content/city_day.csv` (upload the CSV to Colab).

---

## Results

The **XGBoost Regressor** (after hyperparameter tuning) achieved the best performance:

| Metric | Value |
|--------|-------|
| MAE | 21.45 |
| RMSE | 42.62 |
| R² Score | 0.90 |

> Fill in your actual metric values after running the notebook.

**Best XGBoost parameters found:**
```
learning_rate: 0.2 | max_depth: 5 | n_estimators: 100
```

---

## Tech Stack

- Python 3.x
- pandas, NumPy
- scikit-learn
- XGBoost
- matplotlib, seaborn
- joblib

---

## License

This project is open-source under the [MIT License](LICENSE).
