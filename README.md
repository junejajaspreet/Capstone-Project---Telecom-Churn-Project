# Capstone-Project---Telecom-Churn-Project
1. Telecom Churn Case Study
1.1 Problem Statement
1.1.1 Business Problem Overview
The telecom sector is highly competitive, with customers having the freedom to switch service providers easily. This dynamic market experiences an annual churn rate of 15-25%. Given that acquiring new customers costs significantly more than retaining existing ones—5 to 10 times more—customer retention has become a critical focus for telecom companies.

For most established operators, retaining profitable customers is a primary business objective.

To minimize churn, telecom companies need to predict which customers are most likely to leave.

This project aims to analyze customer data from a leading telecom company, develop predictive models to identify customers at risk of churn, and uncover the key drivers of churn.

1.2 Understanding and Defining Churn
The telecom industry offers two primary billing models: postpaid (customers receive a bill monthly or annually after using services) and prepaid (customers pay in advance to use services).

In the postpaid model, customers typically notify their operator before leaving, making it easy to identify churn.

However, in the prepaid model, customers can leave without notifying the operator, making it harder to determine if they have truly churned or if they are temporarily inactive (e.g., traveling abroad for a while).

Predicting churn is particularly challenging for prepaid customers, and the definition of churn must be carefully considered. Prepaid is more common in India and Southeast Asia, while postpaid is dominant in Europe and North America.

This project focuses on the Indian and Southeast Asian markets.

1.3 Definitions of Churn
Churn can be defined in various ways, such as:

Revenue-based churn: Customers who have not used any revenue-generating services like mobile internet, outgoing calls, or SMS within a given period. For instance, customers who generate less than INR 4 per month in total or average revenue could be considered churned.

However, this definition may miss customers who only receive calls or SMS from family members in rural areas, who may not generate revenue but still use services.

Usage-based churn: Customers who have not engaged in any usage—such as calls or internet access—over a specified time.

One drawback of this definition is that by the time a customer stops using services, it may be too late to intervene and prevent churn. For example, if churn is defined by zero usage for two months, the customer may have already switched operators by then.

In this project, we will use usage-based churn to define churn.

1.4 High-value Churn
In India and Southeast Asia, the top 20% of customers contribute to around 80% of revenue. Therefore, reducing churn among high-value customers is critical for minimizing significant revenue loss.

This project will define high-value customers using a specific metric (as explained below) and will focus on predicting churn among these high-value customers.

1.5 Understanding the Business Objective and the Data
The dataset contains customer-level data for four consecutive months—June, July, August, and September. The months are encoded as 6, 7, 8, and 9, respectively.

The objective is to predict churn in the last month (September) using data from the first three months (June, July, and August). To achieve this effectively, it's important to understand customer behavior leading up to churn.

1.6 Understanding Customer Behavior During Churn
Customers usually don’t switch providers abruptly but rather go through different stages (especially high-value customers). In churn prediction, the customer lifecycle is divided into three phases:

The ‘good’ phase: The customer is satisfied with the service and behaves normally.

The ‘action’ phase: Customer satisfaction starts to decline, often due to a competitor’s attractive offer, unjust charges, or poor service quality. Customers exhibit different behaviors during this phase, and identifying high-churn-risk customers is vital, as corrective actions (such as matching offers or improving service) can still be taken.

The ‘churn’ phase: This phase marks when the customer has churned. Churn is defined based on this phase. It's important to note that during prediction, data from this phase is not available. Therefore, after identifying churned customers (churn=1, otherwise 0), all churn phase-related data is discarded.

In this case, the first two months represent the ‘good’ phase, the third month represents the ‘action’ phase, and the fourth month is the ‘churn’ phase.

1.7 Data Dictionary
The data dictionary explains abbreviations commonly used in the dataset, such as loc (local), IC (incoming), OG (outgoing), T2T (telecom-to-telecom), T2O (telecom-to-other operator), RECH (recharge), etc.

Columns with suffixes 6, 7, 8, and 9 represent data from months 6, 7, 8, and 9.

1.8 Data Preparation
The data preparation involves several crucial steps:

Feature Engineering: This involves deriving new features based on business understanding, which could serve as important indicators of churn.

Identifying High-value Customers: We will focus on predicting churn for high-value customers. These are defined as customers who have recharged an amount greater than or equal to the 70th percentile of the average recharge amount during the good phase (first two months).

Tagging Churners and Removing Churn Phase Attributes: Churned customers are those who did not make any calls (incoming or outgoing) or use mobile internet during the churn phase (fourth month). The relevant attributes for this are:

total_ic_mou_9
total_og_mou_9
vol_2g_mb_9
vol_3g_mb_9
After tagging churners, we remove all churn-phase data (attributes with '_9').

1.9 Modelling
We will build predictive models for churn based on high-value customers to achieve two goals:

Predict which customers are likely to churn, allowing the company to take proactive steps such as offering special plans or discounts.

Identify key variables that predict churn, helping the business understand why customers switch to competitors.

Given the large number of features, we will first apply dimensionality reduction using PCA and then use a classification model to predict churn. Additionally, we will address class imbalance (since churn rates are typically low) using appropriate techniques.

The steps for model building include:

Preprocess the data (e.g., handling missing values and formatting columns).
Conduct exploratory analysis to uncover useful insights.
Engineer new features.
Apply PCA for dimensionality reduction.
Train and fine-tune various models, addressing class imbalance.
Evaluate models using metrics that prioritize churn prediction accuracy.
Select the best model based on performance.
To identify the most important predictors, a separate model will be built using logistic regression or decision trees. These models will help identify key churn indicators and provide actionable insights.

Lastly, we will recommend strategies for reducing churn based on the findings.

