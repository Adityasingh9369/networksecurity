
# Network Security Threat Detection – Machine Learning Pipeline

## Overview
This project implements an **end-to-end machine learning pipeline** for detecting malicious or anomalous network traffic.  
The focus of the project is on **robust ML pipeline design**, **reproducible training**, **experiment tracking**, and **batch inference**, rather than production deployment.

The system covers the complete ML lifecycle:
- Data ingestion
- Data validation
- Data transformation
- Model training and evaluation
- Experiment tracking using MLflow
- Batch prediction using trained artifacts

---

## Problem Statement
Network security systems generate large volumes of traffic data, making it difficult to manually identify malicious activity.  
The goal of this project is to **classify network traffic as normal or malicious** using supervised machine learning techniques.

---

## Project Architecture

networksecurity/
│
├── components/
│ ├── data_ingestion.py
│ ├── data_validation.py
│ ├── data_transformation.py
│ └── model_trainer.py
│
├── pipeline/
│ ├── training_pipeline.py
│ └── batch_prediction.py
│
├── utils/
│ ├── ml_utils/
│ │ ├── model/
│ │ └── metric/
│ └── main_utils/
│
├── entity/
│ ├── config_entity.py
│ └── artifact_entity.py
│
├── final_model/
│ ├── model.pkl
│ └── preprocessor.pkl
│
├── artifact/
├── logs/
├── main.py
└── README.md


---

## Machine Learning Workflow

### 1. Data Ingestion
- Data is ingested from a MongoDB source
- Raw data is stored as artifacts for traceability

### 2. Data Validation
- Schema validation
- Missing value checks
- Data consistency checks

### 3. Data Transformation
- Feature engineering
- Data preprocessing using `scikit-learn`
- Preprocessor saved as a reusable artifact

### 4. Model Training
Multiple classification models are trained and evaluated:
- Random Forest
- Decision Tree
- Gradient Boosting
- Logistic Regression
- AdaBoost

The best-performing model is selected based on evaluation metrics.

### 5. Evaluation Metrics
The following metrics are computed:
- Accuracy
- Precision
- Recall
- F1-score

Metrics are encapsulated in a `ClassificationMetricArtifact` and tracked using **MLflow**.

---

## Experiment Tracking (MLflow + DAGsHub)

All experiments are tracked using **MLflow**, integrated with **DAGsHub**.

Tracked information includes:
- Evaluation metrics (accuracy, precision, recall, F1-score)
- Model artifacts
- Experiment runs and comparisons

You can view experiments and runs here:
https://dagshub.com/Adityasingh9369/networksecurity.mlflow


---

## Model Performance (Example)

> Update these values from MLflow after final training.

- **Accuracy:** 0.9728
- **F1-score:** 0.9758
- **Precision:** 0.9703
- **Recall:** 0.9813

---

## How to Run the Project

### 1. Create Virtual Environment
bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

###2. Run Training Pipeline
python main.py


This will:

Train the model

Evaluate performance

Log metrics to MLflow

Save trained artifacts

###3. Run Batch Prediction
python networksecurity/pipeline/batch_prediction.py


Predictions are generated using the trained model and preprocessor.

Why This Project Is Not Deployed

This project intentionally focuses on:

ML pipeline design

Experiment tracking

Offline training and batch inference

Deployment was kept out of scope to prioritize:

Clean architecture

Reproducibility

ML engineering fundamentals

The trained model can be deployed later if required.

Tech Stack

Python

Pandas, NumPy

Scikit-learn

MLflow

DAGsHub

MongoDB

FastAPI (local inference only)

Future Improvements

Hyperparameter optimization

Model explainability (SHAP, LIME)

Online inference API

CI/CD for ML pipelines

Model monitoring and drift detection

Author

Aditya Singh
B.Tech Student | Machine Learning & Data Structures


