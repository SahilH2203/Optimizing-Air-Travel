# Optimizing-Air-Travel

# ✈️ Air Travel Delay Prediction

## 📌 Project Overview

Flight delays cause major inconvenience to passengers and significant financial costs to airlines.
This project focuses on **predicting flight delays** using historical air travel data, analyzing both **occurrence of delays (classification)** and **delay duration (regression)**.

The project not only builds accurate predictive models but also uses **SHAP explainability** to identify controllable factors, ensuring actionable recommendations for airlines.

---

## 🎯 Objectives

* Analyze historical flight data to uncover delay trends.
* Predict **delay occurrence (Yes/No)** using classification models.
* Predict **delay duration (minutes)** using regression models.
* Use **SHAP explainability** to interpret model predictions.
* Identify **controllable vs. external causes** of delays.
* Provide **operational recommendations** to reduce delays.

---

## 📂 Repository Structure

```
air-travel-delay-prediction/
├── data/                # Dataset and column definitions
├── notebooks/           # Jupyter Notebook with complete code
├── reports/             # Final report (PDF)
├── requirements.txt     # Project dependencies
├── README.md            # Documentation
└── .gitignore
```

---

## 🔎 Data and Preprocessing

* **Dataset:** Historical flight-level data with multiple features (airline, airport, month, delays, etc.).
* **Column definitions:** Provided in `data/column_definitions.pdf`.
* **Key preprocessing steps:**

  * Removed outcome-leakage features (post-flight delays, cancellations, diversions).
  * Created new pre-flight features:

    * `carrier_delay_rate` → average delay % per airline
    * `airport_delay_rate` → average delay % per airport
    * `route_delay_rate` → delay % for each route
    * `season` → one-hot encoded seasonal labels
  * Ensured models use only **pre-flight features** for realistic predictions.

---

## 🤖 Modeling Approach

### Classification (Delay Occurrence)

* Algorithms tested: Logistic Regression, Random Forest, XGBoost
* **Best Model:** XGBoost

  * Accuracy: **95%**
  * F1 Score: **0.97**

### Regression (Delay Duration in Minutes)

* Algorithm: Gradient Boosting Regressor
* **Performance:**

  * MAE: ~10.5 minutes
  * RMSE: ~18.5 minutes
  * R² Score: 0.74

---

## 🔍 Model Interpretability (SHAP)

* **Top influential features:**

  1. `arr_flights` (airport arrivals)
  2. `route_delay_rate` (historical route delay)
  3. `season` (seasonal trends)
  4. `airport_delay_rate`, `carrier_delay_rate`

* **Operational Action Index (OAI):**

  * 93.91% of model’s weighted focus is on **controllable delays**.
  * Ensures recommendations are actionable for airline operations.

---

## 📈 Results & Insights

* **Controllable Delay Sources:** Late aircraft turnaround, carrier issues (crew, maintenance, gate).
* **External Delay Sources:** Weather, NAS (airspace), security.
* **Actionable Recommendations:**

  * Improve turnaround efficiency at key hubs.
  * Enhance crew scheduling and maintenance planning.
  * Smarter routing to avoid congested NAS corridors.
  * Communicate anticipated risks (weather/NAS) proactively to passengers.

---

## 🚀 How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/username/air-travel-delay-prediction.git
   cd air-travel-delay-prediction
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebook:

   ```bash
   jupyter notebook notebooks/flight_delay_notebook.ipynb
   ```

---

## 🛠️ Technologies Used

* Python (Pandas, NumPy, Matplotlib, Seaborn)
* Scikit-learn
* XGBoost
* Gradient Boosting Regressor
* SHAP for interpretability
* Jupyter Notebook

---

## 📑 Reports

* Detailed methodology and analysis: [`presentation_deck/Presentation.pdf`](presentation_deck/Presentation.pdf)
* Dataset description: [`Dataset/Column_definitions.pdf`](Dataset/Column_definitions.pdf)
