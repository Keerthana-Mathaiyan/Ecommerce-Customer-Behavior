# Ecommerce-Customer-Behavior


## Overview


This project analyzes an e-commerce dataset to gain insights into customer behavior and predict business outcomes. It focuses on customer churn prediction, segmentation, lifetime value forecasting, and recommendation systems.


The dataset is sourced from Kaggle and contains detailed information about customer demographics, engagement, purchase history, and behavioral metrics.

## Project Goals

    1.Binary Classification (Churn Prediction)
    
    Predict whether a customer will churn (Churned) based on engagement, purchase, and demographic data.
    
    2.Customer Segmentation (Clustering)
    
    Group customers into clusters based on behavior and engagement metrics for targeted marketing strategies.
    
    3.Lifetime Value Forecasting (Regression)
    
    Predict customer lifetime value (Lifetime_Value) to optimize retention and marketing spend.
    
    4.Recommendation Systems
    
    Suggest products to users based on purchase history and engagement data (collaborative filtering/SVD).

## 🧹Data Cleaning & Preprocessing

    ⚡Missing numerical values filled with median.
    
    ⚡Missing categorical values filled with "Unknown".
    
    ⚡Unrealistic or negative values were clipped (e.g., Age, Total_Purchases).
    
    ⚡Behavioral engagement metrics were processed and standardized.
    
    ⚡Optional features include PCA and cluster labels for advanced analysis.

## Outputs

    ecommerce_clean_for_powerbi.xlsx – cleaned dataset ready for visualization and Power BI.

       
    Jupyter notebooks with preprocessing, regression, clustering, and feature analysis.

## Power BI DAX


Core Customer KPIs (Measures)

    1.Total Customers = COUNTROWS(Customers)
    
    2.Active Customers =
    CALCULATE(
        COUNTROWS(Customers),
        Customers[Churned] = 0
    )
    
    3.Churned Customers =
    CALCULATE(
        COUNTROWS(Customers),
        Customers[Churned] = 1
    )
    
    4.Churn Rate % =
    DIVIDE(
        [Churned Customers],
        [Total Customers]
    )



Revenue & Value Measures

    1.Total Lifetime Value =
    SUM(Customers[Lifetime_Value])
    
    2. Average Lifetime Value =
    AVERAGE(Customers[Lifetime_Value])
    
    
    3. Average Order Value =
    AVERAGE(Customers[Average_Order_Value])
    
    
    4. Avg Purchases per Customer =
    AVERAGE(Customers[Total_Purchases])



Engagement Measures

    1.Avg Login Frequency =
    AVERAGE(Customers[Login_Frequency])
    
    2. Avg Session Duration =
    AVERAGE(Customers[Session_Duration_Avg])
    
    4. Avg Pages Per Session =
    AVERAGE(Customers[Pages_Per_Session])
    
    6. Avg Email Open Rate =
    AVERAGE(Customers[Email_Open_Rate])
    
    8. Avg Social Engagement =
    AVERAGE(Customers[Social_Media_Engagement_Score])


Retention & Recency Measures

    1.Avg Membership Years =
    AVERAGE(Customers[Membership_Years])
    
    2.Avg Days Since Last Purchase =
    AVERAGE(Customers[Days_Since_Last_Purchase])


Churn vs Behavior Measures


    1.Churn Rate by Segment % =
    DIVIDE(
        CALCULATE(COUNTROWS(Customers), Customers[Churned] = 1),
        COUNTROWS(Customers)
    )
    
    2. Avg Login Frequency (Churned) =
    CALCULATE(
        AVERAGE(Customers[Login_Frequency]),
        Customers[Churned] = 1
    )
    
    3. Avg Login Frequency (Active) =
    CALCULATE(
        AVERAGE(Customers[Login_Frequency]),
        Customers[Churned] = 0
    )


Discount, Returns & Support

   
    1.Avg Discount Usage Rate =
    AVERAGE(Customers[Discount_Usage_Rate])
    
    2. Avg Returns Rate =
    AVERAGE(Customers[Returns_Rate])
    
    4. Avg Customer Service Calls =
    AVERAGE(Customers[Customer_Service_Calls])



Calculated Columns (Segmentation)

🎯 Age Group

    
    Age Group =
    SWITCH(
        TRUE(),
        Customers[Age] < 25, "18–24",
        Customers[Age] < 35, "25–34",
        Customers[Age] < 45, "35–44",
        Customers[Age] < 55, "45–54",
        "55+"
    )


💰 Customer Value Segment

    
    Customer Value Segment =
    SWITCH(
        TRUE(),
        Customers[Lifetime_Value] >= 10000, "High Value",
        Customers[Lifetime_Value] >= 5000, "Medium Value",
        "Low Value"
    )


🔥 Engagement Level

    
    Engagement Level =
    SWITCH(
        TRUE(),
        Customers[Login_Frequency] >= 20 &&
        Customers[Session_Duration_Avg] >= 10, "High Engagement",
        Customers[Login_Frequency] >= 10, "Medium Engagement",
        "Low Engagement"
    )


⚠️ Churn Risk Flag (Business Logic)


    Churn Risk =
    IF(
        Customers[Days_Since_Last_Purchase] > 90 &&
        Customers[Login_Frequency] < 5,
        "High Risk",
        "Low Risk"
    )



📉 High-Risk Churn %

    
    High Risk Churn % =
    DIVIDE(
        CALCULATE(
            COUNTROWS(Customers),
            Customers[Churned] = 1,
            Customers[Days_Since_Last_Purchase] > 90
        ),
        [Total Customers]
    )



📱 Mobile App Usage vs Churn

   
    Mobile Users Churn Rate % =
    DIVIDE(
        CALCULATE(
            COUNTROWS(Customers),
            Customers[Churned] = 1,
            Customers[Mobile_App_Usage] = 1
        ),
        CALCULATE(
            COUNTROWS(Customers),
            Customers[Mobile_App_Usage] = 1
        )
    )


## ⚙️Tools & Libraries

    Python: pandas, numpy, scikit-learn, matplotlib, seaborn
    
    Excel: for Power BI integration
    
    GitHub: version control and sharing

## How to Use

Clone the repository:

    git clone https://github.com/YOUR_USERNAME/ecommerce-churn-analysis.git


Open the notebooks in Jupyter or VS Code.

Use ecommerce_clean_for_powerbi.xlsx for Power BI dashboards and visualizations.

### License:

Database: Kaggle - Open Database,
Contents: Database Contents

Link: [Ecommerce Customer Behavior Dataset](https://www.kaggle.com/datasets/dhairyajeetsingh/ecommerce-customer-behavior-dataset/data)

