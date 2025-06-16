# 🎧 Beatit.ai - Customer Churn Prediction

## Overview

**Beatit.ai** is a leading South Asian music streaming platform serving millions of users via free, ad-supported, and subscription models. With rising churn rates due to increased competition and macroeconomic shifts, this project aims to **predict the propensity of customer churn** using user activity and interaction logs. The ultimate goal is to enable **proactive retention strategies** and ensure sustainable growth.

This repository walks through the full ML lifecycle—from experimentation to productionization—using **MLflow** for model tracking and **Airflow** for orchestration.

---

## 📌 Problem Statement

To build a model that can predict which users are likely to **churn** (i.e., not renew their subscription) based on historical interaction, transaction, and membership data. This enables Beatit.ai to take **preemptive actions** and improve customer retention.

---

## 🔧 Project Structure

The project progresses through four key stages using Jupyter notebooks:

1. **`1_Data_preparation.ipynb`**
   Initial data loading and basic preprocessing to prepare for model building.

2. **`2_ModelBaseline.ipynb`**
   Baseline churn prediction model using existing features to assess feasibility.

3. **`3_Feature_engineering.ipynb`**
   Extensive feature engineering, such as:

   * Counting unique payment methods instead of averaging them
   * Creating derived features like `discount` (difference between plan price and actual payment)
   * Exploring hypothesis-driven features to improve prediction accuracy

4. **`4_Model_after_feature_engg.ipynb`**
   Final model training using **LightGBM**, hyperparameter tuning, and evaluation.

---

## ⚙️ Experiment Tracking with MLflow

We used **MLflow** for:

* Logging metrics and model versions
* Comparing different experiments and tuning configurations
* Tracking the full training process from feature creation to model deployment readiness

---

## 🔄 Moving to Production: Airflow Pipelines

After model selection, we automate the full workflow using **Apache Airflow**:

* Load raw data
* Apply preprocessing and feature engineering
* Generate predictions using the trained model
* Store outputs in a production-ready format

### Why Airflow?

* **Reusability**: Apply the same steps on any new data automatically
* **Agility**: Reduce manual effort and streamline deployment
* **Modularity**: Customize or replace components easily

You’ll find examples of DAGs and operators configured for the churn prediction pipeline.

---

## 💡 Key Learnings

* Avoid statistical missteps, such as averaging categorical IDs (e.g., `payment_method_id`). Instead, count transactions and unique methods used.
* Derived features like `discount` can reveal important behavioral insights.
* MLflow and Airflow together provide a solid base for scalable, reproducible ML systems.

---

## 📁 Directory Structure

```
📦 BeatitChurnPrediction/
├── 1_Data_preparation.ipynb
├── 2_ModelBaseline.ipynb
├── 3_Feature_engineering.ipynb
├── 4_Model_after_feature_engg.ipynb
├── airflow/
│   ├── dags/
│   └── config/
├── mlruns/                # MLflow experiment tracking data
├── models/                # Saved trained models
├── data/                  # Raw and processed datasets
└── README.md
```

---

## 🚀 Getting Started

1. Clone this repo:

   ```bash
   git clone [https://github.com/your-username/beatit-churn-prediction.git](https://github.com/ManikeshYBoyini/ML_Ops.git)
   cd ML_Ops
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Run notebooks in order to train and evaluate the model.

4. Launch MLflow UI:

   ```bash
   mlflow ui
   ```

5. Start Airflow for orchestration:

   ```bash
   airflow db init
   airflow webserver --port 8080
   airflow scheduler
   ```

---

## 📊 Tech Stack

* **Python**
* **Pandas, NumPy, Scikit-learn**
* **LightGBM**
* **MLflow** – for experiment tracking
* **Optuna** – for hyperparameter tuning
* **Airflow** – for pipeline orchestration
* **Jupyter** – for development and prototyping

---

## ✨ Future Enhancements

* Integrate model inference into a real-time dashboard
* Set up model drift monitoring in production
* Automate daily/weekly retraining jobs

---

## 📬 Contact

For questions, feel free to reach out or open an issue.

