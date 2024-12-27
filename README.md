# PWC-task-2---Customer-Churn-analysis

## **Table of Content**
- [Problem Statement](#problem-statement)
- [Data Source](#data-source)
- [Data Preparation](#data-preparation)
- [Data Analysis(DAX)](#data-analysis-dax)
- [Data Visualization Dashboard](#data-visualization-dashboard)
- [Insights](#insights)


## **Problem Statement**

The client has reached out with a critical request to visualize their data effectively. They are seeking insights that can be easily understood and actionable, requiring a blend of technical expertise and creativity. The challenge lies in:

    Identifying Key Metrics: Understanding the client's business context to determine the most relevant metrics for their needs.

    Designing Clear Visualizations: Creating intuitive, engaging, and actionable dashboards using Power BI.

    Delivering Insights: Transforming raw data into a narrative that highlights trends, anomalies, and opportunities for the client to make data-driven decisions.
## **Data Source**
Dataset used for this task was presented by Pwc and customer churn Retention dataset:
Dataset :[Dataset](https://github.com/nehajade03/PWC-task-2---Customer-Churn-analysis/blob/main/Customer%20Churn-Dataset.xlsx)

## **Data Preparation**
-The Customer Churn dataset, consisting of 23 columns and 7,043 rows, was transformed and prepared for modeling in Microsoft Power BI Desktop using Power Query. 
Adding a New Column:

A conditional column named loyalty was created using the M-formula, categorizing customers based on their tenure:

- loyalty = SWITCH(TRUE(),'ChurnDataset'[tenure]<=12,"< 1 year",'01 Churn-Dataset'[tenure]<=24,"< 2 years",'01 Churn-Dataset'[tenure]<=36,"< 3 years",'01 Churn-Dataset'[tenure]<=48,"< 4 years", '01 Churn-Dataset'[tenure]<=60,"< 5 years",'01 Churn-Dataset'[tenure]<=72,"< 6 years")

- Each of the columns in the table were validated to have the correct data type

## **Data Analysis (Dax)**

- churn rate % = DIVIDE (CALCULATE(COUNT('Churn Dataset'[Churn]), 'Churn Dataset'[Churn] = "yes" ),CALCULATE ( COUNT ('Churn Dataset'[Churn]), ALLSELECTED ('Churn Dataset'[Churn] ) ))

- Count of Churn for Yes = CALCULATE(COUNTA('Churn Dataset'[Churn]), 'Churn Dataset'[Churn] IN { "Yes" })

- Count of DeviceProtection for Yes = CALCULATE(COUNTA('Churn Dataset'[DeviceProtection]),'Churn Dataset'[DeviceProtection] IN { "Yes" })

- Count of MultipleLines for Yes = CALCULATE(COUNTA('Churn Dataset'[MultipleLines]),'Churn Dataset'[MultipleLines] IN { "Yes" })

- Count of OnlineBackup for Yes = CALCULATE(COUNTA('Churn Dataset'[OnlineBackup]),'Churn Dataset'[OnlineBackup] IN { "Yes" })

- Count of OnlineSecurity for Yes = CALCULATE(COUNTA('Churn Dataset'[OnlineSecurity]),'Churn Dataset'[OnlineSecurity] IN { "Yes" })

- Count of PhoneService for Yes = CALCULATE(COUNTA('Churn Dataset'[PhoneService]),'Churn Dataset'[PhoneService] IN { "Yes" })

- Online Sec. in % = DIVIDE(CALCULATE(COUNT('Churn Dataset'[OnlineSecurity]), 'Churn Dataset'[OnlineSecurity]="Yes",'ChurnDataset'[Churn]="Yes"),CALCULATE(COUNT('ChurnDataset'[OnlineSecurity]),'ChurnDataset'[Churn]="Yes"),0)

- Phone Service in % = DIVIDE(CALCULATE(COUNT('Churn Dataset'[PhoneService]), 'Churn Dataset'[PhoneService]="Yes", 'Churn Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn Dataset'[PhoneService]),'Churn Dataset'[Churn]="Yes"),0)

- Streaming Movies in % = DIVIDE(CALCULATE(COUNT('Churn Dataset'[StreamingMovies]), 'Churn Dataset'[StreamingMovies]="Yes", 'Churn Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn Dataset'[StreamingMovies]),'Churn Dataset'[Churn]="Yes"),0)

- Streaming Movies in % = DIVIDE(CALCULATE(COUNT('Churn Dataset'[StreamingMovies]), 'Churn Dataset'[StreamingMovies]="Yes", 'Churn Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn Dataset'[StreamingMovies]),'Churn Dataset'[Churn]="Yes"),0)

- Tech Support in % = DIVIDE(CALCULATE(COUNT('Churn Dataset'[TechSupport]), 'Churn Dataset'[TechSupport]="Yes", 'Churn Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn Dataset'[TechSupport]),'Churn Dataset'[Churn]="Yes"),0)

## **Data Visualization Dashboard**

Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop:

Dashboard: [Live DashBoard](https://app.powerbi.com/groups/me/reports/eb881247-8074-40f0-99e5-efc7001f8bf6/7181f392639793d2c785?experience=power-bi)

![image](https://github.com/user-attachments/assets/6b85d626-446b-4c4e-87a0-da0bb2bb0559)

![image](https://github.com/user-attachments/assets/b2d50993-4809-41e9-87d2-262724baeac0)

![image](https://github.com/user-attachments/assets/975bc982-effa-4716-b88e-34280635064e)

## **Insights**:

- The churn between male and female customers is balanced, with 939 males and 930 females. Gender does not seem to be a significant factor contributing to churn.
Payment Methods Impact:

- Electronic check payments have the highest churn rate (57.3%), indicating a problem with the ease or reliability of this payment method.

- Mailed checks also have a notable churn rate, whereas credit card payments have the lowest churn rate (12.41%).

- Month-to-month contracts show the highest churn rate (1.7K), while one-year and two-year contracts have significantly lower churn rates.

- Customers on long-term contracts (one year or more) are more loyal than those on flexible month-to-month plans.

- New customers (0-1 year) show the highest churn, suggesting they are more likely to leave early in their subscription period.

- Loyalty is stronger among customers with subscriptions of 4-5 years.

- Fiber optic users experience the highest churn rate (24.5%), followed by DSL users (6.05%). Customers without internet service show a much lower churn rate (69.4%).


- Higher monthly charges correlate with higher churn rates, indicating that customers who pay more might be more sensitive to perceived value or service quality.

## **Recommendations**:

- Since electronic check payments have the highest churn rate, consider improving the payment processing system for this method.
 It might involve addressing transaction failures, offering alternative payment options, or improving user instructions for easier payments.

- Encourage customers to sign one-year or two-year contracts by offering incentives like discounts or additional benefits for longer-term commitments. This could help reduce churn for customers currently on month-to-month plans.

- Given the high churn rate among fiber optic users, investigate service issues like bandwidth, connection quality, or pricing. Offer incentives such as improved service packages, better support, or discounts to retain these customers.


- To combat churn among new customers (0-1 years), enhance the onboarding process with better support, tutorials, and welcome offers. Provide special benefits or rewards to make them feel valued early on, increasing the likelihood of them staying longer.

- Consider revising the pricing model to offer more tiered options, especially for customers with high monthly charges. Providing options for customers with varied needs (e.g., reduced charges for loyal customers or customized packages) could reduce churn.
  

- Identify high-risk groups, such as those on month-to-month contracts or using electronic check payment, and reach out to them proactively. Personalized support or retention offers could help keep them satisfied and reduce churn.

- Implement loyalty programs for customers in the 4-5 year subscription period, offering them exclusive benefits to keep them engaged for even longer periods. You can also target those who are about to reach the 1-year mark with retention offers.

























