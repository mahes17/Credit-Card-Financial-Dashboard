# Credit-Card-Financial-Dashboard
-----------------------
Project overview:
-----------------------
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

---------------------------------------------------------
Steps Used to Create Dashboard:
---------------------------------------------------------
1)	Data Export 
2)	Data Cleaning
3)	Data Transformation
4)	Data processing and DAX Queries
5)	Dashboard and Insights
6)	Export and share Project

1)	Import data from CSV files into Power bi tool.
2)	Cleaned the blank rows, removed duplicates, formatted data types, excluded those columns which is not required etc.
3)	Once the data looks great after all the changes in power query editor then loaded by close and apply.
4)	Created the Measures and New columns as per the requirement with the help of DAX Queries.
5)	Created the two dashboard one for Crediit card report and other dashboard created for Customer credit card transaction report.
6)	Export the data and share the insights to the clients and stake holders.

   
-----------------------------------------------------------------------
DAX Queries used:
-----------------------------------------------------------------------

Age Group = SWITCH(
    TRUE(),
    customer[Customer_Age] < 30,"20=30",
    customer[Customer_Age] >= 30 && customer[Customer_Age] < 40, "30-40",
    customer[Customer_Age] >= 40 && customer[Customer_Age] < 50, "40-50",
    customer[Customer_Age] >= 50 && customer[Customer_Age] < 60, "50-60",
    customer[Customer_Age] >= 60,"60+",
    "Unknown")

Income Group = SWITCH(TRUE(),
customer[Income] <35000, "Low",
customer[Income] >=35000 && customer[Income] <70000 ,"Med",
customer[Income] >=70000, "High",
"Unknown")

Week_num2 = WEEKNUM(credit_card[Week_Start_Date].[Date])

Revenue = credit_card[Annual_Fees]+credit_card[Total_Trans_Amt]+credit_card[Interest_Earned]

Current_week_rev = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(ALL(credit_card),credit_card[Week_num2]= MAX(credit_card[Week_num2])))

Previous_week_rev = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(ALL(credit_card),credit_card[Week_num2]= MAX(credit_card[Week_num2])-1))

-----------------------------------------------------------------------
Insight :
-----------------------------------------------------------------------

Week of Week Change:
•	Revenue decreased by 12.8%.
•	Total Transaction Amount and Count is decreased by 0.26 & 0.21%.
•	Customer Count decreased by 0.03%.
•	Customer Satisfaction Score decreased by 1.03%.

Overview of YTD :
•	Overall revenue is 55.3M
•	Total interest is 7.8M
•	Total transaction amount is 45M
•	Male customers are contributing more in revenue 30M,female 25M
•	Blue and Silver credit card are contributing to 93% of overall transactions
•	TX, NY & CA states are contributing to 68%
•	Overall activation rate is 57.47 %
•	Overall delinquent rate is 6.07%


