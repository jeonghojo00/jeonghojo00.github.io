---
layout: post
title: 'Salifort Motors'
date: 2023-06-17 00:50:00 -0500
categories: [machine learning, classification]
tags: [machine learning, data analytics, classification, imbalanced dataset, exploratory data analysis, random forest, xgboost, naive bayes]
---

# Salifort Motors Project 
[Code](https://github.com/jeonghojo00/GoogleAdvancedDataAnalytics/blob/ce49c14c94dd97840ddb0c1b8c6441adf355a6b5/Capstone%20Project/Salifort%20Motors%20project%20lab.ipynb)

## Description and Deliverables
### Description
In this capstone project, I had the opportunity to delve into data analysis and predictive modeling to provide valuable insights to the Human Resources (HR) department of a large consulting firm (imaginary company). 

Throughout this project, I worked on a comprehensive dataset, employing various techniques to build predictive models. The primary objective was to create a tool that can effectively predict whether an employee is likely to leave the company. 

By leveraging machine learning models, I aimed to offer actionable information to HR professionals, enabling them to make informed decisions regarding employee retention strategies.

### Main Questions to Answer and Hypothesis
- Can we predict whether an employee is likely to leave the company?
    - Yes. I hypothesized that it is possible to develop predictive models that can accurately forecast whether an employee is likely to leave the company.
- What are the key factors influencing employee retention?
    - By identifying and analyzing key factors, such as employee satisfaction, tenure, salary, and performance, we can gain valuable insights into the drivers of employee retention.


## Data Analysis
I decided to explore and analyze data by data types. Main the EDA will have 6 parts
1. Dataset overview
2. Distribution of Target values (Left or Stayed)
3. Analyze the distribution and summary statistics of numeric features
4. Examine the distribution of categorical features
5. Correlation analysis
6. Continuous exploration

### 1. Dataset Overview
1. There are 14,999 rows, 10 columns, and these variables:

Variable  |Description |
-----|-----| 
satisfaction_level|Employee-reported job satisfaction level [0&ndash;1]|
last_evaluation|Score of employee's last performance review [0&ndash;1]|
number_project|Number of projects employee contributes to|
average_monthly_hours|Average number of hours employee worked per month|
time_spend_company|How long the employee has been with the company (years)
Work_accident|Whether or not the employee experienced an accident while at work
left|Whether or not the employee left the company
promotion_last_5years|Whether or not the employee was promoted in the last 5 years
Department|The employee's department
salary|The employee's salary (U.S. dollars)

### 2. Distribution of Target values (Left or Stayed)
![Employee Attrition](/assets/images/salimotors/salimotors_eda_2_distribution_left.jpg)
Out of all the employees in the dataset, approximately 16.6% have left the company, while the remaining 83.4% have stayed. Considering the imbalanced distribution of the target values, it becomes essential to evaluate our models using appropriate metrics that are robust to class imbalance, such as precision, recall, F1-score, and AUC-ROC. These metrics will provide a comprehensive evaluation of our model's performance in correctly predicting both employees who are likely to leave (true positives) and those who are likely to stay (true negatives).

### 3. Distribution of Numeric Features
![Dist. Numeric Features](/assets/images/salimotors/salimotors_eda_3_distribution_numeric.jpg)

### 4. Distribution of Categorical Features
![Dists. Categorical Features](/assets/images/salimotors/salimotors_eda_4_distribution_categorical.jpg)

### 5. Correlation Analysis
![Correlation](/assets/images/salimotors/salimotors_eda_5_correlation.jpg)
Multicollinearity occurs when two or more variables are highly correlated with each other, which can lead to issues in the interpretation of regression models.

The absence of high multicollinearity is an encouraging finding, as it suggests that the variables in our dataset are relatively independent of each other.

### 6. Feature Interactions
![Feature Interactions 1](/assets/images/salimotors/salimotors_eda_6_features_1.jpg)
1. (Left) 'Last Evaluation' vs. 'Satisfaction Level'
    - It shows that employess who are 'Highly Evaluated' and have 'Low Satisfaction Level' tended to leave.
2. (Right)'Average Monthly Hours' vs. 'Satisfaction Level'
    - It shows that employee who worked 'More' in average and have 'Low Satisfaction Level' tended to leave.
![Feature Interactions 2](/assets/images/salimotors/salimotors_eda_6_features_2.jpg)
3. Employees in HR team left the company the most by ratio and employees in R&D and managment stayed the most by ratio. However, it seems like there were no significant factors that affect whether employees leave the coompany or not.

![Feature Interactions 3](/assets/images/salimotors/salimotors_eda_6_features_3.jpg)
4. It significantly showed that employees with low salary likely to leave the company.


## Classification Model and Results
Model  |Accuracy |Precision |Recall |F1 |AUC_ROC |
-----|-----|-----|-----| -----|-----| 
Naive Bayes |0.825550 |0.462334 |0.663136 |0.544822 |0.759517|
Random Forest |0.985657 |0.982022 |0.925847 |0.953108 |0.961340|
XGBoost |0.985324 |0.973451 |0.932203 |0.952381 |0.963726|

Overall, based on the given results, both Random Forest and XGBoost models demonstrate strong predictive capabilities for identifying employees likely to leave the company. Their high accuracy and balanced precision-recall trade-off make them suitable choices for this particular prediction task.

![Feature Importance RF](/assets/images/salimotors/salimotors_feature_importance_rf.jpg)
![Feature Importance XGBoost](/assets/images/salimotors/salimotors_feature_importance_xgb.jpg)

Interestingly both models showed that the top 5 most importance features were 'satisfaction_level', number_project', 'average_monthly_hours', 'time_spend_company', and 'last evaluation'. 

## Suggestion
Based on the analysis and feature importance results, here are some suggestions that can be addressed to the company's HR team:

1. Focus on Employee Satisfaction: 
    - The 'satisfaction_level' is identified as the most important feature in predicting employee attrition. It suggests that the level of satisfaction plays a crucial role in an employee's decision to leave the company. The HR team should pay close attention to employee satisfaction and take measures to improve it. Regular employee feedback surveys, open communication channels, and addressing concerns promptly can contribute to enhancing employee satisfaction.

2. Work-Life Balance: 
    - Factors like 'number_project' and 'average_monthly_hours' indicate that excessive workload and long working hours may contribute to employee attrition. The HR team should consider implementing strategies to promote a healthy work-life balance. This can include workload management, flexible work arrangements, and encouraging employees to take regular breaks.

3. Career Growth and Development:
    - The 'time_spend_company' feature suggests that employees who have spent a significant amount of time in the company are more likely to leave. This could indicate a lack of career growth opportunities or employee burnout. The HR team should focus on providing clear career paths, professional development opportunities, and mentoring programs to retain experienced employees.

4. Performance Evaluation and Feedback: 
    - The 'last_evaluation' feature highlights the importance of fair and regular performance evaluations. HR should ensure that performance evaluations are conducted objectively and provide constructive feedback to employees. Regular performance discussions can help identify and address any issues or concerns before they lead to employee dissatisfaction.

5. Employee Retention Strategies:
    - Considering the top five important features, the HR team should design and implement employee retention strategies. These strategies can include improving the work environment, offering competitive compensation and benefits, recognizing and rewarding employee achievements, promoting a positive company culture, and fostering a supportive and inclusive workplace.

It's important for the HR team to regularly monitor these factors, gather employee feedback, and adapt strategies accordingly. By addressing these suggestions, the company can increase employee satisfaction, reduce attrition rates, and foster a positive and engaging work environment.








