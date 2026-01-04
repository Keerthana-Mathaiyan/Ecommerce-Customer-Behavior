# Ecommerce-Customer-Behavior


##Overview


This project analyzes an e-commerce dataset to gain insights into customer behavior and predict business outcomes. It focuses on customer churn prediction, segmentation, lifetime value forecasting, and recommendation systems.


The dataset is sourced from Kaggle and contains detailed information about customer demographics, engagement, purchase history, and behavioral metrics.

##Project Goals

    1.Binary Classification (Churn Prediction)
    
    Predict whether a customer will churn (Churned) based on engagement, purchase, and demographic data.
    
    2.Customer Segmentation (Clustering)
    
    Group customers into clusters based on behavior and engagement metrics for targeted marketing strategies.
    
    3.Lifetime Value Forecasting (Regression)
    
    Predict customer lifetime value (Lifetime_Value) to optimize retention and marketing spend.
    
    4.Recommendation Systems
    
    Suggest products to users based on purchase history and engagement data (collaborative filtering/SVD).

##🧹Data Cleaning & Preprocessing

    ⚡Missing numerical values filled with median.
    
    ⚡Missing categorical values filled with "Unknown".
    
    ⚡Unrealistic or negative values were clipped (e.g., Age, Total_Purchases).
    
    ⚡Behavioral engagement metrics were processed and standardized.
    
    ⚡Optional features include PCA and cluster labels for advanced analysis.

Outputs

    ecommerce_clean_for_powerbi.xlsx – cleaned dataset ready for visualization and Power BI.

       
    Jupyter notebooks with preprocessing, regression, clustering, and feature analysis.

⚙️Tools & Libraries

    Python: pandas, numpy, scikit-learn, matplotlib, seaborn
    
    Excel: for Power BI integration
    
    GitHub: version control and sharing

How to Use

Clone the repository:

    git clone https://github.com/YOUR_USERNAME/ecommerce-churn-analysis.git


Open the notebooks in Jupyter or VS Code.

Use ecommerce_clean_for_powerbi.xlsx for Power BI dashboards and visualizations.
