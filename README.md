# Urban Flood Prediction Using Machine Learning

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-success.svg)

## 📋 Project Overview

This project develops and compares machine learning models to predict urban flood risk in New Orleans using 15 years of historical weather data from NOAA. The goal is to provide early warning capabilities for flood events based on precipitation patterns and weather conditions.

**Author:** Subramani Mokkala   
**Date:** October 2025  

## 🎯 Objectives

- Analyze 15 years of historical weather and flood event data
- Engineer features capturing multi-day precipitation accumulation
- Build and compare classical ML and deep learning models
- Identify key predictors of urban flood risk
- Provide insights for climate adaptation and disaster management

## 📊 Dataset

**Weather Data:**
- **Source:** NOAA Climate Data Online (GHCND)
- **Station:** New Orleans Louis Armstrong International Airport
- **Period:** January 2010 - October 2025 (5,753 days)
- **Variables:** Daily precipitation, temperature (max/min), wind speed, weather type codes

**Flood Events:**
- **Source:** NOAA Storm Events Database
- **Events:** 163 flash flood events
- **Unique Flood Days:** 67 (1.16% of dataset)
- **Period:** 2010-2025

## 🔬 Methodology

### Data Processing
1. **Data Collection:** Downloaded weather and flood event data from NOAA
2. **Data Cleaning:** Handled missing values (< 0.2% of data)
3. **Target Variable:** Binary classification (flood vs non-flood day)
4. **Feature Engineering:** Created 40 features including:
   - Rolling window aggregations (3/7/14/30-day precipitation sums)
   - Lag features (1-3 day precipitation history)
   - Temporal features (month, season, hurricane season indicator)
   - Weather type indicators
   - Derived metrics (temperature range, averages)

### Models Evaluated
1. **Logistic Regression** (baseline with balanced class weights)
2. **Random Forest** (ensemble method)
3. **XGBoost** (gradient boosting)

### Evaluation Metrics
- ROC-AUC Score (primary metric for imbalanced data)
- Precision, Recall, F1-Score
- Confusion Matrix
- Feature Importance Analysis

## 📈 Results

### Model Performance

| Model | ROC-AUC | Recall (Flood) | Precision (Flood) | Key Strength |
|-------|---------|----------------|-------------------|--------------|
| **Logistic Regression** | **0.920** ✅ | **61.5%** | 6% | Best flood detection |
| XGBoost | 0.890 | 0% | - | High overall accuracy |
| Random Forest | 0.874 | 7.7% | 17% | Feature interpretability |

**Winner:** Logistic Regression
- Achieved highest ROC-AUC score (0.920)
- Successfully identified 61.5% of flood events
- Best balance for early warning system (prioritizes recall)

### Key Findings

**Most Important Predictors:**
1. **Same-day precipitation (PRCP)** - Primary indicator
2. **3-day cumulative precipitation** - Soil saturation effect
3. **Previous day's rain (lag1)** - Temporal dependency
4. **Thunder occurrence (WT03)** - Storm severity
5. **7-day precipitation patterns** - Extended accumulation

**Insights:**
- Multi-day precipitation accumulation is critical (18 flood days had <10mm same-day rain)
- Flood risk peaks in May and July (hurricane season impact)
- Average precipitation on flood days: 44.9mm vs 4.0mm on non-flood days
- Temperature patterns provide supplementary context

## 📁 Repository Structure
```
urban-flood-prediction/
├── data/
│   ├── raw/                          # Original NOAA data files
│   └── processed/                    # Engineered features dataset
├── notebooks/
│   ├── 01_data_exploration.ipynb    # EDA and feature engineering
│   └── 02_model_building.ipynb      # Model training and evaluation
├── results/
│   ├── visualizations/              # Plots and charts
│   └── model_performance_comparison.csv
├── README.md
└── requirements.txt
```

## 🛠️ Technologies Used

- **Python 3.8+**
- **Data Processing:** pandas, NumPy
- **Machine Learning:** scikit-learn, XGBoost
- **Visualization:** Matplotlib, Seaborn
- **Data Sources:** NOAA Climate Data Online, NOAA Storm Events Database

## 🚀 How to Run

1. **Clone the repository:**
```bash
git clone https://github.com/SubramaniMokkala/urban-flood-prediction.git
cd urban-flood-prediction
```

2. **Install dependencies:**
```bash
pip install -r requirements.txt
```

3. **Run notebooks:**
```bash
jupyter notebook
```

4. **Execute in order:**
   - `01_data_exploration.ipynb` - Data loading, EDA, feature engineering
   - `02_model_building.ipynb` - Model training and comparison

## 💡 Future Enhancements

- **Real-time prediction:** Integrate weather forecast APIs
- **Spatial analysis:** Add elevation and urban infrastructure data
- **Deep learning:** Implement LSTM for temporal sequence modeling
- **Multi-city:** Extend to Houston, Miami for generalization testing
- **Deployment:** Create web application for early warning system

## 📊 Visualizations

### Precipitation Patterns
- Flood vs non-flood day precipitation distributions
- Time series analysis with flood events marked
- Monthly flood frequency patterns

### Model Performance
- ROC curves for all models
- Confusion matrices
- Feature importance rankings

## 📚 References

- NOAA Climate Data Online: https://www.ncei.noaa.gov/cdo-web/
- NOAA Storm Events Database: https://www.ncdc.noaa.gov/stormevents/
- Relevant research papers on urban flood prediction and ML applications

## 📧 Contact

**Subramani Mokkala**
- Email: [subramanimokkala@gmail.com]
- LinkedIn: [SubramaniMokkala](www.linkedin.com/in/subramani-mokkala-727683245)
- GitHub: [@SubramaniMokkala](https://github.com/SubramaniMokkala)

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- NOAA for providing comprehensive climate and storm event data
- scikit-learn and XGBoost communities for excellent ML libraries

---

**⭐ If you found this project interesting, please consider giving it a star!**
```

**Save this as your new README.md**

---

### **Task 2: Update requirements.txt**

Make sure it has all dependencies:
```
pandas==1.5.3
numpy==1.24.3
scikit-learn==1.2.2
xgboost==2.0.0
matplotlib==3.7.1
seaborn==0.12.2
jupyter==1.0.0
```

---

### **Task 3: Add a LICENSE file**

Create `LICENSE` file (MIT License):
```
MIT License

Copyright (c) 2025 Subramani Mokkala

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
