# NoShowPredictionModel Week5
HealthConnect Clinic — No-Show Prediction Model
AnalystLab Africa Experience Lab | Data Science Track
Python Jupyter Status Track

Project Overview
HealthConnect Clinic is a fictional healthcare provider that manages appointment-based services. This project uses data and machine learning to predict patient no-shows — helping the clinic reduce missed appointments, optimise appointment slot usage, and direct patient support more effectively.

Project question: How can HealthConnect Clinic use data and AI to reduce missed appointments and improve the patient support experience?

This repository contains the Data Science track contribution to the HealthConnect Experience Lab project, covering exploratory data analysis, data preprocessing, feature engineering, and baseline model development.

Project Status
Week	Focus	Status
Week 4	Problem definition, resource review, solution planning	✅ Complete
Week 5	EDA, preprocessing, feature engineering, baseline model	✅ Complete
Week 6	Improved modelling, feature importance, hyperparameter tuning	🔄 Upcoming
Key Results — Week 5 Baseline
Metric	Value
Model	Logistic Regression (class_weight='balanced')
Recall	0.603
Precision	0.668
F1-Score	0.634
ROC-AUC	0.680
These results establish the performance benchmark for all future models. Any Week 6 model must exceed F1: 0.634 / ROC-AUC: 0.680 to be considered an improvement.

Repository Structure
healthconnect-no-show-prediction/
│
├── data/
│   ├── raw/
│   │   └── HealthConnect_Appointment_Data.csv        # Original dataset (read-only)
│   └── processed/
│       └── healthconnect_binary_processed.csv        # Preprocessed modelling dataset
│
├── notebooks/
│   └── Week5_HealthConnect_DS_Baseline.ipynb         # Main Week 5 notebook
│
├── reports/
│   ├── Week5_DS_Baseline_Report.md                   # Full baseline modelling report
│   └── Week5_Project_Summary.md                      # Week 5 project summary
│
├── .gitignore
├── requirements.txt
└── README.md
Dataset
File: HealthConnect_Appointment_Data.csv

The dataset contains 5,000 fictional and anonymised appointment records with the following key fields:

Category	Columns
Patient demographics	patient_id, gender, age, age_group
Appointment details	appointment_id, appointment_type, appointment_day, appointment_time, appointment_date
Booking information	booking_date, booking_lead_days
Historical behaviour	previous_appointments, previous_no_shows
Reminder information	reminder_sent, reminder_channel
Logistical factors	distance_to_clinic_km, waiting_time_minutes
Target	appointment_outcome (Attended / No-Show / Cancelled)
Important: The original dataset must not be overwritten. All processed or derived files are saved separately under data/processed/.

Approach
1. Exploratory Data Analysis
Inspected dataset shape, data types, missing values, and duplicates
Analysed target variable distribution (No-Show: 48.5% / Attended: 46.3% / Cancelled: 5.3%)
Produced univariate and bivariate visualisations across numerical and categorical features
Generated a correlation heatmap for numerical features
2. Data Preprocessing
Excluded Cancelled records → binary modelling dataset: 4,737 records
Dropped redundant/identifier columns: appointment_id, patient_id, age_group, booking_date, appointment_date
Applied one-hot encoding to categorical variables (fitted on training data only)
Applied median imputation to distance_to_clinic_km and waiting_time_minutes (medians from training data only)
3. Train / Validation / Test Split
Patient-level split (70% train / 20% validation / 10% test)
Splitting on unique patient_id prevents data leakage from patients appearing in multiple sets
4. Feature Engineering
Feature	Formula	Purpose
no_show_rate	previous_no_shows / previous_appointments	Normalises no-show history relative to total appointment count; more informative than raw counts alone
5. Baseline Model
Logistic Regression (class_weight='balanced', max_iter=1000, random_state=42)
Evaluated on the validation set using Recall, Precision, F1-Score, ROC-AUC, Confusion Matrix, and feature coefficient analysis
Setup & Installation
Requirements
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
Install dependencies:

pip install -r requirements.txt
Running the Notebook
Option A — Jupyter Notebook:

jupyter notebook notebooks/Week5_HealthConnect_DS_Baseline.ipynb
https://colab.research.google.com/drive/1Zzd3KE6fZ6jH6pMakc9YLVSgcJuG5uwy?usp=drive_link
df = pd.read_csv('path/to/HealthConnect_Appointment_Data.csv')
Tech Stack
Tool	Purpose
Python 3.10+	Core programming language
Pandas	Data manipulation and analysis
NumPy	Numerical operations and feature engineering
Matplotlib / Seaborn	Data visualisation
Scikit-learn	Preprocessing, modelling, and evaluation
Jupyter Notebook / Google Colab	Interactive development environment
GitHub	Version control and project documentation
Week 6 Plan
Train and evaluate a Random Forest classifier
Apply feature scaling (StandardScaler)
Conduct formal feature importance analysis
Explore SMOTE for handling class imbalance
Hyperparameter tuning via cross-validation
Engineer additional features (is_new_patient flag, ordinal time encoding)
Evaluate final model on held-out test set
Produce comparative evaluation: Logistic Regression vs Random Forest
Limitations
Dataset is fictional — model patterns may not generalise to real clinic data
reminder_channel has 27.3% missing values — encoding approach is documented but may not fully capture reminder effectiveness
New patients (previous_appointments = 0) are assigned no_show_rate = 0 — a dedicated is_new_patient flag is proposed for Week 6
No feature scaling applied at baseline — to be addressed in Week 6
Test set is reserved and has not yet been evaluated
Project Resources
Resource	File
Appointment Dataset	HealthConnect_Appointment_Data.csv
[HealthConnect_Appointment_Data.csv](https://github.com/user-attachments/files/32101201/HealthConnect_Appointment_Data.csv)

Data Dictionary	HealthConnect_Data_Dictionary.xlsx
Clinic Knowledge Base	HealthConnect_Clinic_Knowledge_Base.docx
[HealthConnect_Clinic_Knowledge_Base.docx.pdf](https://github.com/user-attachments/files/32101347/HealthConnect_Clinic_Knowledge_Base.docx.pdf)

About This Project
This project is part of the AnalystLab Africa Experience Lab Internship Programme. HealthConnect Clinic and all associated data are entirely fictional and created for educational purposes.

Intern: Christina Nompomelelo Sebueng Track: Data Science Programme: AnalystLab Africa Experience Lab

#AnalystLabAfrica
