# Machine Learning Project - Muhammad Adi Nugroho

## Project Domain

Customer churn prediction involves identifying customers likely to leave a service or cancel their subscription. This prediction is crucial for many businesses, as acquiring new customers is often more costly than retaining existing ones. Each lost customer represents a loss of investment, requiring time and effort to replace them. Accurately predicting when a customer is likely to churn and offering incentives to retain them can save a company significant financial resources.

Different customers exhibit different behaviors, making it time-consuming to manually analyze whether a customer will churn. Therefore, it is essential for a business to automate the prediction of customer churn. The predictions can then be used to create attractive offers or incentives.

Reference: [Customer Churn](https://www.avaus.com/blog/predicting-customer-churn/#:~:text=Predicting%20Customer%20Churn,more%20than%20retaining%20existing%20ones.)

## Business Understanding

### Problem Statements

1. High customer churn rates may indicate service deficiencies or inadequate promotions. Thus, telecom companies need to understand the factors driving customers to unsubscribe.
2. Identifying patterns and trends associated with customer churn can help companies anticipate and prevent customer loss. Success in this area depends on effectively managing and analyzing customer data.

### Goals

1. Identify key factors contributing to customer churn. Understanding these factors enables companies to take appropriate actions to improve customer retention and reduce churn rates.
2. Develop a predictive model that can accurately forecast customer churn. This allows companies to take preventive measures swiftly to retain at-risk customers.

### Solution Statements

1. Conduct exploratory data analysis, including univariate and multivariate analysis, to identify factors influencing churn.
2. Create several machine learning models to compare and determine which model better predicts churn.

## Data Understanding

The dataset used in this project can be accessed at [Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn?resource=download).

### Dataset Information

- Format: CSV
- Samples: 7043
- Features: 21 (3 numeric, the rest categorical)
- Missing Values: Yes

### Customer Churn Dataset Variables

- Customer ID
- Gender: Customer's gender (Male, Female)
- Senior Citizen: Whether the customer is a senior citizen (1, 0)
- Partner: Whether the customer has a partner (Yes, No)
- Dependents: Whether the customer has dependents (Yes, No)
- Tenure: Number of months the customer has stayed with the company
- PhoneService: Whether the customer has phone service (Yes, No)
- MultipleLines: Whether the customer has multiple lines (Yes, No, No phone service)
- InternetService: Customer’s internet service provider (DSL, Fiber optic, No)
- OnlineSecurity: Whether the customer has online security (Yes, No, No internet service)
- OnlineBackup: Whether the customer has online backup (Yes, No, No internet service)
- DeviceProtection: Whether the customer has device protection (Yes, No, No internet service)
- TechSupport: Whether the customer has tech support (Yes, No, No internet service)
- StreamingTV: Whether the customer has streaming TV (Yes, No, No internet service)
- StreamingMovies: Whether the customer has streaming movies (Yes, No, No internet service)
- Contract: The contract term of the customer (Month-to-month, One year, Two year)
- PaperlessBilling: Whether the customer has paperless billing (Yes, No)
- PaymentMethod: The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
- MonthlyCharges: The amount charged to the customer monthly
- TotalCharges: The total amount charged to the customer
- Churn: Whether the customer churned (Yes, No)

## Data Preparation

Data preparation involves several steps:

1. Ensure no duplicates and handle missing values to prepare data for machine learning.
2. Add features to enhance model performance, derived from existing features.
3. Split the data into training and test sets before encoding to avoid data leakage.
4. Create a pipeline for data processing, including one-hot encoding for categorical data, standard scaling for numeric data, and label encoding for the target column.

## Modeling

Several machine learning models were used to predict churn:

- **Random Forest**: An ensemble of decision trees. Parameters used:
  - `n-estimator`: Number of trees
  - `max depth`: Maximum depth of each tree
  - `random state`: Seed for randomness

- **K-Nearest Neighbors (KNN)**: Simple algorithm that looks at the nearest neighbors of a data point. Parameters used:
  - `n-neighbors`: Number of neighbors considered for classification
  - `weights`: Weights assigned to each neighbor

- **Logistic Regression**: Uses a logistic function for classification. 
  Formula:
  $$P = \frac{1}{1 + e^{-(b_0 + b_1 \times X)}}$$
  - `random state`: Seed for randomness

- **AdaBoostClassifier**: An ensemble technique. Parameters used:
  - `n-estimator`: Number of trees
  - `random state`: Seed for randomness

Logistic Regression performed the best in this project, with higher metric values compared to other models. It is also simple and fast.

## Evaluation

Precision and F1-score were used to evaluate the model's performance:

- **Precision**: Indicates how many predicted positives are actual positives.
  $$Precision = \frac{TP}{TP + FP}$$

- **F1-Score**: Harmonic mean of precision and recall.
  $$F1-Score = 2 \times \frac{(precision \times recall)}{(precision + recall)}$$

  - TP: True Positives
  - FP: False Positives

### Model Evaluation Results

| Model                | Precision | Recall | F1-Score | Accuracy |
|----------------------|-----------|--------|----------|----------|
| Random Forest        | 0.62      | 0.48   | 0.54     | 0.78     |
| KNN                  | 0.57      | 0.55   | 0.56     | 0.77     |
| Logistic Regression  | 0.67      | 0.57   | 0.61     | 0.81     |
| AdaBoost             | 0.65      | 0.53   | 0.58     | 0.80     |

Logistic Regression outperformed other models in detecting customer churn with an accuracy of 81%.
