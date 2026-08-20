# 📊 Predicting Customer Churn in the Indian Telecom Industry

> An end-to-end Machine Learning project for identifying customers at risk of churn in the Indian telecommunications industry using customer demographics, service usage, account information, and behavioral attributes.

---

## 🚀 Project Overview

Customer churn is a major challenge for telecommunications companies. Retaining existing customers is often more valuable than acquiring new ones, making accurate churn prediction an important business problem.

This project develops a complete **Machine Learning classification pipeline** to predict whether a telecom customer is likely to churn.

The project covers the complete workflow from **data understanding and exploratory analysis to preprocessing, feature engineering, model comparison, hyperparameter tuning, customer-level prediction, and model interpretation**.

### 🔄 End-to-End Machine Learning Pipeline

```text
Raw Data
   ↓
Data Understanding & Validation
   ↓
Exploratory Data Analysis
   ↓
Data Cleaning
   ↓
Feature Engineering
   ↓
Categorical Encoding
   ↓
Feature Scaling
   ↓
Train/Test Split
   ↓
SMOTE Class Balancing
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Hyperparameter Tuning
   ↓
Final Model Selection
   ↓
Customer Churn Prediction
   ↓
Model Interpretation
```

---

## 🎯 Business Objective

The primary objective is to identify customers who are at higher risk of leaving a telecom service.

The resulting churn prediction system can support businesses in:

* Identifying high-risk customers
* Improving customer retention
* Supporting targeted marketing campaigns
* Prioritizing customer-support efforts
* Reducing customer attrition
* Improving customer lifetime value
* Supporting data-driven retention strategies

### 💼 Business Problem

```text
Customer Data
     ↓
Analyze Customer Behavior
     ↓
Predict Churn Risk
     ↓
Identify High-Risk Customers
     ↓
Take Retention Actions
     ↓
Improve Customer Retention
```

---

# 📊 Dataset

**Dataset:** Telecom Churn Dataset
**Domain:** Indian Telecommunications
**Source:** Kaggle
**Target Variable:** `churn`

The dataset contains:

* **100,000 customer records**
* **14 original columns**

The dataset includes customer demographics, telecom partner information, registration details, account information, and service-usage attributes.

---

## 📋 Dataset Features

| Feature                | Description                               |
| ---------------------- | ----------------------------------------- |
| `customer_id`          | Unique customer identifier                |
| `telecom_partner`      | Customer's telecom service provider       |
| `gender`               | Customer gender                           |
| `age`                  | Customer age                              |
| `state`                | Customer state                            |
| `city`                 | Customer city                             |
| `pincode`              | Customer postal code                      |
| `date_of_registration` | Customer registration date                |
| `num_dependents`       | Number of customer dependents             |
| `estimated_salary`     | Estimated customer salary                 |
| `calls_made`           | Number of calls made                      |
| `sms_sent`             | Number of SMS messages sent               |
| `data_used`            | Data usage                                |
| `churn`                | Target variable indicating customer churn |

---

# 🔍 Exploratory Data Analysis

Exploratory Data Analysis was performed to understand customer behavior and identify relationships between customer characteristics and churn.

### EDA Areas

* Churn class distribution
* Age distribution
* Tenure distribution
* Telecom partner distribution
* Data usage distribution
* Churn rate by telecom partner
* Tenure vs churn
* Age vs churn
* Calls vs churn
* SMS usage vs churn
* Data usage vs churn
* Churn rate by number of dependents
* Data usage vs calls
* Registration-month churn analysis
* Multivariate relationship analysis

The analysis showed that churn represents a significant minority class, making appropriate classification and class-imbalance handling important.

---

## 📊 Churn Distribution

---

## 📈 Tenure vs Churn

---

# 🧹 Data Preprocessing

A structured preprocessing workflow was implemented before model training.

## 🔎 Data Quality Checks

The dataset was checked for:

* Missing values
* Duplicate records
* Outliers
* Data consistency

### Results

* **Missing values:** None found
* **Duplicate records:** None found

---

# 🛠️ Feature Engineering

The original registration date was transformed into meaningful features.

### Created Features

* `tenure_days`
* `registration_month`

The original `date_of_registration` column was then removed.

### Removed Identifier / High-Cardinality Features

The following columns were removed from the modeling dataset:

* `customer_id`
* `city`
* `pincode`

These fields were not considered useful predictive features for the model.

---

# 🔤 Categorical Encoding

Categorical variables were converted into numerical representations.

### Encoding Strategy

**Binary Encoding**

* `gender`

**One-Hot Encoding**

* `telecom_partner`
* `state`

This allowed categorical information to be incorporated into the Machine Learning models.

---

# 📏 Feature Scaling

Numerical/model features were standardized using:

```text
StandardScaler
```

Feature scaling was applied to ensure that numerical variables were represented on a comparable scale for models that are sensitive to feature magnitude.

---

# ⚖️ Class Imbalance Handling

Because churn represents a minority class, **SMOTE (Synthetic Minority Over-sampling Technique)** was applied to the training data.

### After SMOTE

| Class     |     Samples |
| --------- | ----------: |
| Class 0   |      50,322 |
| Class 1   |      50,322 |
| **Total** | **100,644** |

SMOTE was applied to the training data to avoid using synthetic observations from the test set.

---

# 🤖 Machine Learning Models

Multiple classification algorithms were trained and evaluated.

### Models Evaluated

1. Logistic Regression
2. K-Nearest Neighbors (KNN)
3. Support Vector Classifier (SVC)
4. Decision Tree
5. Random Forest
6. Bagging Classifier
7. Gradient Boosting
8. XGBoost
9. Tuned Logistic Regression

This model comparison provides a broader evaluation instead of relying on a single algorithm.

---

# 📈 Model Evaluation

The models were evaluated using multiple classification metrics:

* Accuracy
* Precision
* Recall
* F1-Score
* Classification Report
* Confusion Matrix

For model comparison, **Test F1-Score** was used as the primary ranking metric.

---

## 🏆 Model Performance

| Rank | Model                           | Test F1-Score |
| ---: | ------------------------------- | ------------: |
| 🥇 1 | **Logistic Regression (Tuned)** |    **0.9073** |
|    2 | Logistic Regression (Base)      |        0.9072 |
|    3 | SVC                             |        0.9055 |
|    4 | XGBoost                         |        0.9031 |
|    5 | Gradient Boosting               |        0.8979 |
|    6 | Random Forest                   |        0.8849 |
|    7 | Bagging                         |        0.8711 |
|    8 | Decision Tree                   |        0.8546 |
|    9 | KNN                             |        0.8328 |

### Key Finding

The tuned Logistic Regression model achieved the highest test F1-score:

> **F1-Score: 0.9073**

The improvement over the base Logistic Regression model was marginal but positive.

---

## 📊 Model Comparison

---

# 🏆 Final Model

## Logistic Regression with Hyperparameter Tuning

After comparing multiple Machine Learning algorithms, **Tuned Logistic Regression** was selected as the final model.

### Final Test Performance

| Metric        | Performance |
| ------------- | ----------: |
| **Accuracy**  |        ~91% |
| **Precision** |        ~91% |
| **Recall**    |        ~91% |
| **F1-Score**  |   **~0.91** |

The tuned model achieved a test F1-score of **0.9073**.

The training and test performance were very similar in this experiment, indicating good generalization on the available test data.

---

# 📊 Confusion Matrix

The confusion matrix provides a detailed view of the model's classification results and helps evaluate how effectively the model identifies churned and retained customers.

---

# 🔮 Customer-Level Churn Prediction

The project includes reusable prediction functionality that can accept customer information and generate a churn prediction.

### Prediction Output

The prediction system provides:

* Churn prediction
* Churn / Retained label
* Retention probability
* Churn probability

### Example Workflow

```text
Customer Information
        ↓
Preprocessing
        ↓
Feature Transformation
        ↓
Trained Logistic Regression Model
        ↓
Churn Probability
        ↓
Customer Risk Classification
```

---

## 👤 Example Customer Predictions

### Profile A — New Customer with Low Usage

```text
Prediction: Churned
```

This example demonstrates how the model can identify a customer profile with higher churn risk.

### Profile B — Long-Term Customer with High Usage

```text
Prediction: Retained
```

This example demonstrates how the model can classify a customer profile with lower churn risk.

---

# 🧠 Model Interpretation

The project also includes an explanation function for the Logistic Regression model.

The function calculates **feature contributions for individual predictions**, helping understand which model features contribute toward a customer's predicted churn outcome.

This improves model transparency and provides an interpretable view of individual predictions.

---

# 🛠️ Technologies & Tools

### Programming

* Python

### Data Analysis

* Pandas
* NumPy

### Data Visualization

* Matplotlib
* Seaborn

### Machine Learning

* Scikit-learn
* XGBoost
* imbalanced-learn

### Machine Learning Techniques

* Logistic Regression
* KNN
* SVC
* Decision Tree
* Random Forest
* Bagging
* Gradient Boosting
* XGBoost
* SMOTE
* Hyperparameter Tuning
* Feature Scaling
* Categorical Encoding

### Development Environment

* Jupyter Notebook
* Google Colab

### Model Utilities

* Joblib

---

# 📁 Project Structure

```text
Predicting-Customer-Churn-Indian-Telecom/
│
├── 📓 Predicting_Customer_Churn_in_the_Indian_Telecom_Industry.ipynb
│
├── 📊 images/
│   ├── 01_churn_distribution.png
│   ├── 02_tenure_vs_churn.png
│   ├── 03_model_comparison.png
│   └── 04_confusion_matrix.png
│
├── 📄 README.md
├── 📦 requirements.txt
├── ⚖️ LICENSE
└── 🚫 .gitignore
```

---

# 🚀 How to Run the Project

## 1. Clone the Repository

```bash
git clone <your-repository-url>
```

Navigate into the project directory:

```bash
cd Predicting-Customer-Churn-Indian-Telecom
```

---

## 2. Install Dependencies

Install the required Python packages:

```bash
pip install -r requirements.txt
```

---

## 3. Open the Notebook

Run Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Predicting_Customer_Churn_in_the_Indian_Telecom_Industry.ipynb
```

---

# ☁️ Google Colab

The project was developed using **Google Colab** and can also be executed in a Google Colab environment.

### Dataset Configuration

The notebook currently loads the dataset from a local/Colab path.

If another user wants to reproduce the project, the dataset path must be configured according to their environment.

---

# 📌 Key Insights

The project demonstrates that customer churn prediction can be approached as a supervised binary classification problem.

Important aspects of the project include:

* Data quality validation
* Exploratory Data Analysis
* Feature engineering
* Categorical encoding
* Feature scaling
* Class imbalance handling
* Comparison of multiple classification algorithms
* Hyperparameter tuning
* Model evaluation
* Customer-level prediction
* Individual prediction interpretation

---

# 💡 Key Takeaways

### 1. Data Preparation Matters

Proper data validation, feature engineering, encoding, and scaling are important before training Machine Learning models.

### 2. Class Imbalance Requires Attention

SMOTE was used on the training data to balance the minority churn class.

### 3. Model Comparison Is Important

Nine classification approaches were evaluated rather than selecting a model without comparison.

### 4. Logistic Regression Performed Strongly

Logistic Regression achieved the strongest test F1-score in this experiment.

### 5. Hyperparameter Tuning Provided a Small Improvement

The tuned Logistic Regression model improved the F1-score from:

```text
0.9072 → 0.9073
```

### 6. The Model Supports Customer-Level Predictions

The trained system can be used to generate churn/retention predictions and probability estimates for new customer profiles.

### 7. Model Interpretation Improves Transparency

Feature contribution analysis provides additional insight into individual Logistic Regression predictions.

---

# 📈 Project Highlights

| Area                      | Implementation            |
| ------------------------- | ------------------------- |
| **Problem Type**          | Binary Classification     |
| **Domain**                | Indian Telecommunications |
| **Dataset Size**          | 100,000 records           |
| **Original Features**     | 14                        |
| **Target**                | `churn`                   |
| **EDA**                   | ✅                         |
| **Feature Engineering**   | ✅                         |
| **Categorical Encoding**  | ✅                         |
| **Feature Scaling**       | ✅                         |
| **SMOTE**                 | ✅                         |
| **Models Compared**       | 9                         |
| **Hyperparameter Tuning** | ✅                         |
| **Final Model**           | Tuned Logistic Regression |
| **Test F1-Score**         | **0.9073**                |
| **Test Accuracy**         | **~91%**                  |
| **Customer Prediction**   | ✅                         |
| **Model Interpretation**  | ✅                         |

---

# 🎯 Skills Demonstrated

This project demonstrates practical skills relevant to **Data Analyst, Data Scientist, and Machine Learning Engineer** roles.

### Data Analysis

* Data cleaning
* Data validation
* Exploratory Data Analysis
* Statistical/relationship analysis
* Customer behavior analysis

### Machine Learning

* Supervised learning
* Binary classification
* Logistic Regression
* Ensemble models
* Model comparison
* Hyperparameter tuning

### Data Preprocessing

* Feature engineering
* Categorical encoding
* Feature scaling
* Class imbalance handling
* SMOTE

### Model Evaluation

* Accuracy
* Precision
* Recall
* F1-score
* Classification report
* Confusion matrix

### Business Analytics

* Customer churn analysis
* Customer segmentation by risk
* Retention-focused insights
* Business-oriented interpretation of ML predictions

---

# 🔄 Reproducibility

To reproduce the project:

```text
1. Clone repository
2. Install requirements
3. Configure dataset path
4. Open Jupyter Notebook / Google Colab
5. Run the notebook cells
6. Review EDA
7. Execute preprocessing pipeline
8. Train classification models
9. Compare model performance
10. Run hyperparameter tuning
11. Evaluate the final model
12. Test customer-level predictions
```

---

# ⚠️ Important Note

The project uses the Telecom Churn Dataset sourced from Kaggle.

The dataset is not included in this repository. Users reproducing the project will need to obtain the dataset separately and configure the appropriate dataset path in the notebook.

The reported model performance represents the results obtained in this project experiment and may vary depending on the dataset version, preprocessing configuration, random state, and execution environment.

---

# 🔮 Future Improvements

Potential extensions for this project include:

* Deploying the model as a web application
* Building a Streamlit prediction interface
* Creating an interactive customer churn dashboard
* Adding probability-based customer risk tiers
* Performing deeper feature importance analysis
* Adding SHAP-based model explainability
* Implementing automated ML pipelines
* Adding model monitoring
* Connecting the prediction system to a database
* Developing targeted customer retention recommendations

---

# 👨‍💻 Author

## SREEHARI.P

**Data Science | Machine Learning | Data Analytics**

Interested in building data-driven solutions using:

```text
Python
Data Analytics
Machine Learning
SQL
Data Visualization
Business Intelligence
```

---

## ⭐ Project

If you find this project useful, consider giving the repository a ⭐.

```text
Data → Insights → Machine Learning → Prediction → Business Decision
```

