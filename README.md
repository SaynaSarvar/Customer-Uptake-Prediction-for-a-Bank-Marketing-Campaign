# 🎯 Customer Uptake Prediction for a Bank Marketing Campaign

This project develops and evaluates several machine learning models to predict whether a customer will accept a promotional term deposit offer from a financial institution. The goal is to select the best model to help the marketing department optimize its campaign, increase profit, and minimize costs.

---

## 📂 Project Overview

This repository contains the code and analysis for a classification problem based on a historical marketing dataset. The primary challenge is not just achieving high accuracy, but balancing several key business factors:

* **Profit**: Maximizing the number of customers who accept the offer.  
* **Reputational Damage**: Minimizing calls to uninterested customers.  
* **Opportunity Loss**: Reducing the number of potential customers who are incorrectly predicted as "No".  
* **Wasted Costs**: Minimizing money spent contacting customers who ultimately decline the offer.  

The final output is a recommendation for the most effective and efficient model to guide the marketing campaign.

---

## 📊 The Dataset

The dataset includes customer demographic and financial information from previous campaigns. All numerical fields have been standardized.

* **`age`**: Customer's age.  
* **`default`**: Indicates if the customer has credit in default (1 = Yes, 0 = No).  
* **`balance`**: Customer's average annual balance.  
* **`housing`**: Indicates if the customer has a housing loan (1 = Yes, 0 = No).  
* **`loan`**: Indicates if the customer has a personal loan (1 = Yes, 0 = No).  
* **`day`**: Day of the month the customer was last contacted.  
* **`duration`**: Duration of the last contact in seconds.  
* **`y`**: The target variable. Indicates if the customer accepted the offer (1 = Yes, 0 = No).  

---

## ⚙️ Project Workflow

The project follows a standard machine learning pipeline to ensure robust and reliable results.

### 1. Data Exploration 🕵️‍♀️
* **Initial Analysis**: The data was loaded and inspected to check for missing values and understand its structure.  
* **Class Imbalance**: A significant imbalance was identified (**39,922 "No"** vs. **5,289 "Yes"**).  

### 2. Data Preprocessing ⚖️
* **Data Splitting**: Stratified 80/20 split to maintain class distribution.  
* **Handling Imbalance with SMOTE**: The **SMOTE** (Synthetic Minority Over-sampling Technique) was applied **only to the training data**, creating a balanced set to prevent bias.  

### 3. Model Training & Tuning 🧠
The following models were trained and evaluated on the balanced data:  
* **LightGBM**  
* **Random Forest**  
* **Logistic Regression**  
* **Neural Network (MLP Classifier)**  
* **Linear Discriminant Analysis (LDA)**  
* **K-Nearest Neighbors (KNN)**  
* **Quadratic Discriminant Analysis (QDA)**  

### 4. Evaluation 📈
* **Test Set Evaluation**: All models were assessed on the untouched test set.  
* **Key Metrics**: Precision, Recall, and F1 Score guided selection.  
* **Business Interpretation**: Models with high recall but very low precision were avoided due to high campaign costs and reputational risk.  

---

## 🏆 Results and Model Selection

The final performance comparison is summarized below:

| Model                      | Precision | Recall | F1 Score |
| :------------------------- | :-------- | :----- | :------- |
| **LightGBM**               | **0.4700** | **0.5189** | **0.4933** |
| Random Forest              | 0.4525    | 0.4930 | 0.4714   |
| Logistic Regression        | 0.3324    | 0.7495 | 0.4605   |
| Linear Discriminant Analysis | 0.3330    | 0.7259 | 0.4566   |
| Neural Network (MLP)       | 0.3419    | 0.6616 | 0.4509   |
| K-Nearest Neighbors        | 0.2989    | 0.6389 | 0.4072   |
| Quadratic Discriminant Analysis | 0.2243 | 0.8195 | 0.3522   |

---

### ✅ Final Choice: **LightGBM**

The **LightGBM model** was selected as the best performer.

* **Why LightGBM?**  
  - Achieved the **highest F1 Score (0.4933)**.  
  - Balanced **Precision (0.4700)** and **Recall (0.5189)**.  
  - More efficient and effective than Random Forest (second-best).  
  - Outperformed neural networks despite much lower training time.  

This balance is critical to:  
✔️ Capture the maximum number of interested customers (high recall).  
✔️ Reduce wasted calls and costs (solid precision).  
✔️ Minimize reputational damage from over-contacting uninterested customers.  

## 📌 Key Business Takeaway

The **LightGBM model** provides the best trade-off between efficiency and effectiveness, making it the **most reliable choice to guide future bank marketing campaigns**.

---
