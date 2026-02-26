
# Water Quality Classification using Machine Learning
![download](https://github.com/user-attachments/assets/1c86e75e-0ce9-4fd0-a2ed-cf82a933c7da)


## Project Overview

Water quality monitoring is essential for protecting public health and maintaining environmental sustainability. Government agencies classify water bodies into designated use categories such as Class A (drinking water source after disinfection), Class B (outdoor bathing), Class C (drinking water after conventional treatment), and Class E (irrigation and industrial use).

The objective of this project is to build a machine learning classification model that predicts whether a water sample belongs to High Quality Water (Class A) or Lower Quality Water (Classes B, C, and E) using physicochemical and biological parameters.

The goal is to create a stable, interpretable, and generalizable predictive system that can assist in efficient water quality monitoring and public health decision-making.

---

## Dataset Information

The dataset was collected under the National Water Monitoring Programme in Maharashtra.

* Original dataset size: 444 rows and 54 columns
* Final modeling dataset: 342 samples
* Final selected features: 17 important environmental parameters

The dataset includes variables such as Dissolved Oxygen, BOD, COD, Conductivity, Turbidity, Total Coliform, Fecal Coliform, Total Alkalinity, Sulphate, Nitrate Nitrogen, Flow, and others.

Severe class imbalance was observed in the original dataset:

Class A: 288 samples
Class B: 10 samples
Class C: 11 samples
Class E: 33 samples

Due to extremely low samples in Classes B and C, the multiclass classification problem was reformulated into a binary classification task:

0 – High Quality Water (Class A)
1 – Lower Quality Water (Classes B, C, E)

This reformulation ensured more stable and reliable model performance.

---

## Project Workflow

### 1. Data Understanding and Exploratory Analysis

* Checked duplicates and missing values
* Removed columns with extremely high missing percentages
* Converted numeric columns properly and cleaned BDL values
* Performed univariate, bivariate, and multivariate analysis
* Identified strong relationships such as negative correlation between Dissolved Oxygen and BOD
* Conducted hypothesis testing using a one-sample t-test to validate environmental assumptions

---

### 2. Data Preprocessing and Feature Engineering

* Applied median and mode imputation for missing values
* Used log transformation to reduce skewness in chemical parameters
* Created new features such as Pollution Index and BOD/DO Ratio
* Performed one-hot encoding for categorical variables
* Applied an 80–20 stratified train-test split to preserve class distribution
* Removed constant features and highly correlated features (correlation > 0.85)
* Selected the top 17 most important features using Random Forest feature importance

---

### 3. Model Training and Evaluation

Multiple models were tested:

* Logistic Regression
* Random Forest
* XGBoost

The final selected model was XGBoost (default configuration), as it provided the best balance between overall performance and minority class detection.

Test performance:

* Accuracy: 97 percent
* Macro F1-score: 0.94
* ROC-AUC: 0.95
* Minority class recall: 0.82
* Minority class precision: 1.00

The small gap between training and testing performance confirmed minimal overfitting and good generalization.

---

## Model Explainability

Model interpretability was ensured using:

* XGBoost feature importance (gain method)
* SHAP analysis

SHAP analysis showed that the model relies on meaningful environmental indicators such as Flow, Total Alkalinity, Turbidity, Sulphate, and Dissolved Oxygen.

The model captures realistic environmental relationships rather than relying on random patterns.

---

## Real-World Testing

The trained model was saved using joblib and tested on unseen real-world-like samples.

It correctly classified both high-quality and lower-quality water cases, confirming its practical usability.

The model does not replace laboratory testing but acts as a decision-support and screening tool to prioritize potentially risky water samples.

---

## Business Impact

This system can support environmental agencies by:

* Identifying potentially lower-quality water samples early
* Prioritizing inspection and monitoring resources
* Improving response time in water quality management
* Supporting data-driven environmental decision-making

---

## Technologies Used

* Python
* Pandas and NumPy
* Scikit-learn
* XGBoost
* SHAP
* Matplotlib and Seaborn

---

## Future Improvements

* Increase dataset size for full multiclass modeling
* Include seasonal and time-based patterns
* Deploy the model through an API for real-time predictions
* Expand to additional geographical regions

---

## Author

Vimal
Machine Learning and Data Science Enthusiast
