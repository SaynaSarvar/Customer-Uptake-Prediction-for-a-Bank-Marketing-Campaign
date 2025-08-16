🎯 Customer Uptake Prediction for a Bank Marketing Campaign
This project develops and evaluates several machine learning models to predict whether a customer will accept a promotional term deposit offer from a financial institution. The goal is to select the best model to help the marketing department optimize its campaign, increase profit, and minimize costs.

📂 Project Overview
This repository contains the code and analysis for a classification problem based on a historical marketing dataset. The primary challenge is not just achieving high accuracy, but balancing several key business factors:

Profit: Maximizing the number of customers who accept the offer.

Reputational Damage: Minimizing calls to uninterested customers.

Opportunity Loss: Reducing the number of potential customers who are incorrectly predicted as "No".

Wasted Costs: Minimizing money spent contacting customers who ultimately decline the offer.

The final output is a recommendation for the most effective and efficient model to guide the marketing campaign.

📊 The Dataset
The dataset includes customer demographic and financial information from previous campaigns. All numerical fields have been standardized.

age: Customer's age.

default: Indicates if the customer has credit in default (1 = Yes, 0 = No).

balance: Customer's average annual balance.

housing: Indicates if the customer has a housing loan (1 = Yes, 0 = No).

loan: Indicates if the customer has a personal loan (1 = Yes, 0 = No).

day: Day of the month the customer was last contacted.

duration: Duration of the last contact in seconds.

y: The target variable. Indicates if the customer accepted the offer (1 = Yes, 0 = No).

⚙️ Project Workflow
The project follows a standard machine learning pipeline to ensure robust and reliable results.

1. Data Exploration 🕵️‍♀️
Initial Analysis: The data was loaded and inspected to check for missing values and understand its structure.

Class Imbalance: A significant class imbalance was identified (39,922 'No' vs. 5,289 'Yes'), which could bias the models.

2. Data Preprocessing ⚖️
Data Splitting: The dataset was split into an 80% training set and a 20% test set using a stratified split to maintain the class distribution.

Handling Imbalance with SMOTE: The SMOTE (Synthetic Minority Over-sampling Technique) was applied only to the training data to create a balanced set for model training, preventing the model from being biased towards the majority class.

Feature Engineering & Scaling: Advanced features were created and all data was scaled using StandardScaler within a Pipeline to ensure optimal model performance.

3. Model Training & Tuning 🧠
Baseline Models: Several models were trained on the balanced data to establish baseline performance.

Hyperparameter Tuning: An optimized Random Forest was included, and a LightGBM model was introduced, which ultimately proved to be the top performer.

4. Evaluation 📈
Final Comparison: All models were evaluated on the untouched test set.

Key Metrics: The models were compared based on Precision, Recall, and F1 Score to select the best performer according to the business objectives.

🏆 Results and Model Selection
The final performance of each model on the test set is summarized below.

Model

Precision

Recall

F1 Score

LightGBM

0.4700

0.5189

0.4933

Random Forest (Tuned)

0.4151

0.5454

0.4714

Logistic Regression

0.3324

0.7495

0.4605

Support Vector Machine

0.3253

0.7873

0.4603

Linear Discriminant Analysis

0.3330

0.7259

0.4570

K-Nearest Neighbors

0.2988

0.6371

0.4068

Quadratic Discriminant Analysis

0.2243

0.8195

0.3522

Final Choice: 🥇 LightGBM
The LightGBM model was selected as the best performer.

Why?: It achieved the highest F1 Score (0.4933), demonstrating the most effective balance between finding interested customers (Recall) and minimizing wasted calls (Precision). It also had the highest precision, making it the most cost-effective model. This directly addresses the core business problem of maximizing profit while controlling costs and reputational risk.

💡 Future Improvements
To further enhance the model, the following steps are recommended:

Hyperparameter Tuning for LightGBM: Perform an exhaustive hyperparameter search on the winning LightGBM model to potentially unlock even greater performance.

Advanced Feature Engineering: Create more complex interaction features between customer attributes to provide more predictive power to the model.

Collect More Data: Gather more data points, especially for the minority class ('Yes'), to build an even more robust and reliable model.
