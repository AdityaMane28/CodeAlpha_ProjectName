![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/pandas-Data%20Analysis-lightblue?logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)


# 📊 Unemployment in India — EDA & Predictive Modelling

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/pandas-Data%20Analysis-lightblue?logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)

> A data science project analyzing unemployment trends across Indian states (May 2019 – June 2020), including the impact of the COVID-19 lockdown, and building machine learning models to predict the unemployment rate.

---

## 📋 Table of Contents

- [Project Description](#-project-description)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Machine Learning Models](#-machine-learning-models)
- [Results](#-results)
- [Technologies Used](#-technologies-used)
- [License](#-license)

---

## 📝 Project Description

This project performs a comprehensive **Exploratory Data Analysis (EDA)** and **Machine Learning-based prediction** of unemployment rates across 28 Indian states and union territories.

**Key objectives:**
- Understand unemployment trends across Indian regions (Rural vs Urban)
- Visualize the impact of the COVID-19 pandemic on employment
- Engineer meaningful features (Month, Year, Covid Period, Log-Employed)
- Train and compare multiple regression models
- Tune the best-performing model using `RandomizedSearchCV`
- Evaluate predictions using MAE, RMSE, and R² metrics

---

## 📂 Dataset

**Source:** [CMIE (Centre for Monitoring Indian Economy)](https://www.cmie.com/) via [Kaggle](https://www.kaggle.com/datasets/gokulrajkmv/unemployment-in-india)

**File:** `Unemployment in India.csv`

| Column | Description |
|---|---|
| `Region` | Indian state / union territory |
| `Date` | Month-end date (May 2019 – June 2020) |
| `Frequency` | Sampling frequency (Monthly) |
| `Estimated Unemployment Rate (%)` | Target variable — unemployment rate |
| `Estimated Employed` | Number of employed persons |
| `Estimated Labour Participation Rate (%)` | Labour force participation rate |
| `Area` | Rural or Urban |

- **Total records:** 740 (after cleaning)
- **Regions:** 28
- **Date range:** May 2019 – June 2020 (covers pre-COVID and COVID-19 lockdown periods)

---

## 📁 Project Structure

```
unemployment-in-india/
│
├── Unemployment_In_India.ipynb   # Main Jupyter Notebook
├── Unemployment in India.csv     # Dataset (download separately)
├── requirements.txt              # Python dependencies
└── README.md                     # Project documentation
```

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/unemployment-in-india.git
cd unemployment-in-india
```

### 2. Create a Virtual Environment (Optional but Recommended)

```bash
python -m venv venv
source venv/bin/activate       # Linux / macOS
venv\Scripts\activate          # Windows
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the Dataset

Download `Unemployment in India.csv` from [Kaggle](https://www.kaggle.com/datasets/gokulrajkmv/unemployment-in-india) and place it in the project root directory.

---

## 🚀 Usage

### Run in Jupyter Notebook

```bash
jupyter notebook Unemployment_In_India.ipynb
```

### Run in Google Colab

Upload the notebook and the CSV dataset, then run all cells.

---

## 🔍 Exploratory Data Analysis

The EDA section covers:

- **Distribution** of unemployment rate (histogram + KDE)
- **Time-series trend** of average unemployment rate across months
- **Rural vs Urban** comparison (box plot)
- **Correlation heatmap** between unemployment rate, employed count, and labour participation rate
- **Region-wise average unemployment rate** (horizontal bar chart)

> Key Insight: Unemployment rates **spiked dramatically in April–May 2020** due to the COVID-19 nationwide lockdown in India, with some states exceeding 70%.

---

## 🤖 Machine Learning Models

### Feature Engineering

| Feature | Description |
|---|---|
| `Log_Employed` | Log-transformed employed count (reduces skewness) |
| `Labour_Participation_Rate` | Labour force participation rate (%) |
| `Month` | Extracted from the Date column |
| `Year` | Extracted from the Date column |
| `Covid_Period` | Binary flag: 1 if date ≥ April 2020, else 0 |
| `Region` | Categorical (One-Hot Encoded) |
| `Area` | Categorical: Rural / Urban (One-Hot Encoded) |

### Preprocessing Pipeline

- **Numerical features:** `StandardScaler`
- **Categorical features:** `OneHotEncoder` (handle unknown categories)
- Combined using `ColumnTransformer` inside a `Pipeline`

### Models Compared (5-Fold Cross-Validation)

| Model | CV R² | CV RMSE |
|---|---|---|
| **GradientBoosting** ✅ | 0.5961 | 6.53 |
| RandomForest | 0.5204 | 7.06 |
| Ridge | 0.4269 | 7.76 |
| LinearRegression | 0.4248 | 7.77 |
| HistGradientBoosting | 0.2490 | 8.94 |

> **GradientBoostingRegressor** performed best in cross-validation.  
> **RandomForestRegressor** was selected for hyperparameter tuning (also strong performer and tunable).

### Hyperparameter Tuning — RandomForest (`RandomizedSearchCV`)

Best parameters found:
```
n_estimators     : 500
max_depth        : None
min_samples_split: 2
min_samples_leaf : 1
max_features     : 1.0
```

---

## 📈 Results

Final evaluation on the **held-out test set** (20% of data):

| Metric | Score |
|---|---|
| MAE | **3.806** |
| RMSE | **6.637** |
| R² | **0.696** |

**Visualizations generated:**
- Actual vs Predicted scatter plot
- Residuals distribution histogram

---

## 🛠️ Technologies Used

| Library | Version | Purpose |
|---|---|---|
| Python | 3.8+ | Programming language |
| NumPy | ≥1.21 | Numerical computing |
| Pandas | ≥1.3 | Data manipulation |
| Matplotlib | ≥3.4 | Visualizations |
| Seaborn | ≥0.11 | Statistical plots |
| Scikit-learn | ≥1.0 | ML models & preprocessing |
| Joblib | ≥1.0 | Model serialization |
| Jupyter | ≥1.0 | Interactive notebook |

---

## 📄 License

This project is licensed under the **GPL License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- Dataset sourced from CMIE via Kaggle
- Inspired by the need to understand labour market disruptions during COVID-19 in India

---

> ⭐ If you find this project helpful, please consider giving it a star!
