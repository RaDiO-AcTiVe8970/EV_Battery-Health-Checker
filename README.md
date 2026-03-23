# 🔋 EV Battery Health Checker

> A machine learning project that predicts EV battery fault detection based on electrical and operational readings, with models trained and validated on real-world battery data.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter&logoColor=white)
![ML](https://img.shields.io/badge/Machine_Learning-Scikit--Learn-green?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## 📌 Problem Statement

Battery faults in electric vehicles can lead to performance degradation, safety hazards, and unexpected failures. Early detection of battery faults is critical for fleet operators, maintenance teams, and EV owners — yet traditional diagnostics require expensive equipment and specialist expertise.

This project builds a machine learning classifier that detects battery faults using operational sensor readings, making diagnostics accessible without specialised hardware. The model is trained on data calibrated to real-world EV operating conditions.

---

## 🗂️ Dataset

| File | Description |
|---|---|
| `ev.csv` | Primary training dataset — 1,685 records |
| `validation.csv` | Held-out validation set — 199 records |

**Features (9 input variables):**

| Feature | Description |
|---|---|
| `Voltage` | Battery voltage (V) |
| `Current` | Current draw (A) |
| `Temperature` | Operating temperature (°C) |
| `Charge Capacity` | Battery charge capacity (%) |
| `Internal Resistance` | Internal resistance (Ω) |
| `Age in Cycles` | Number of charge/discharge cycles |
| `State of Charge` | Current state of charge |
| `Discharge Time` | Time to discharge |
| `Charge Time` | Time to fully charge |

**Target variable:** `Fault` — Binary label (0 = Normal, 1 = Fault detected)

---

## 🧠 Methodology

```
Raw Data → Exploratory Data Analysis → Feature Engineering → Model Training → Evaluation → Comparison
```

Six machine learning models were trained and evaluated:

| # | Model | Test Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|---|
| 1 | **Random Forest Regressor** | **94.66%** | **93.33%** | 89.91% | **91.59%** |
| 2 | **Random Forest Classifier** | **94.66%** | **93.33%** | 89.91% | **91.59%** |
| 3 | Decision Tree Regressor | 93.77% | 89.29% | 91.74% | 90.50% |
| 4 | Decision Tree Classifier | 92.58% | 88.89% | 88.07% | 88.48% |
| 5 | Logistic Regression | 72.70% | 63.93% | 35.78% | 45.88% |
| 6 | SVM | 67.66% | — | — | — |

✅ **Best model: Random Forest** (both Regressor and Classifier variants) with **94.66% accuracy** on the test set.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computations |
| Scikit-learn | ML model training and evaluation |
| Matplotlib / Seaborn | Data visualisation and confusion matrices |
| Jupyter Notebook | Development environment (Google Colab) |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

### Run the Notebook
```bash
git clone https://github.com/RaDiO-AcTiVe8970/EV_Battery-Health-Checker.git
cd EV_Battery-Health-Checker
jupyter notebook model.ipynb
```

### Making a Prediction
Once the Random Forest model is trained:
```python
import pandas as pd

# Input battery sensor readings
sample = pd.DataFrame([{
    'Voltage': 3.85,
    'Current': 5.0,
    'Temperature': 30,
    'Charge Capacity': 86,
    'Internal Resistance': 0.013,
    'Age in Cycles': 500,
    'State of Charge': 0.7,
    'Discharge Time': 120,
    'Charge Time': 1.0
}])

prediction = model5.predict(sample)
print("Fault Detected:" if prediction[0] == 1 else "Battery Normal")
```

---

## 📊 Results

The Random Forest model achieved the best overall performance:

- **Test Accuracy:** 94.66%
- **Precision:** 93.33%
- **Recall:** 89.91%
- **F1 Score:** 91.59%
- **Confusion Matrix:** 221 true negatives, 98 true positives, 7 false positives, 11 false negatives

Tree-based ensemble methods significantly outperformed linear models (Logistic Regression, SVM), suggesting the relationship between battery sensor readings and fault status is non-linear and benefits from feature interaction modelling.

---

## 🔮 Future Improvements

- [ ] Expand dataset to include more diverse EV models and climate conditions
- [ ] Add time-series modelling to capture battery degradation trends over charge cycles
- [ ] Build a Streamlit or FastAPI web interface for real-time fault prediction
- [ ] Experiment with XGBoost and LightGBM for potential accuracy improvements
- [ ] Deploy as a REST API for integration with EV fleet management systems
- [ ] Investigate feature importance to identify the strongest fault predictors

---

## 👤 Author

**MD. Mohituzzaman Bhuiyan**
Master of Data Science — Adelaide University, Australia

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/mohituzzaman-bhuiyan-98531b159/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/RaDiO-AcTiVe8970)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
