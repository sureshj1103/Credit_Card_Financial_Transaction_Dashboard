# Credit_Card_Financial_Transaction_Dashboard

## Project objective
1. Data from SQL
2. Data processing & DAX
3. Dashboard & insights
4. Export & share project


## Project Objective
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.


## Import data to SQL database
1. Prepare csv file
2. Create tables in SQL
3. import csv file into SQL


## DAX Queries

AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)


week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))


## Project Insights- Week 52 (24th Dec)
WoW change:
• Revenue decreased by -12.8% as compared to week 51,
• Customer count increased by 57%
• Self-employed clients are the most likely to default on their credit limit 27.20%.

## Overview YTD:
• Overall revenue is 55M
• Total interest is 7.8M
• Total transaction amount is 45M
• Male customers are contributing more in revenue 30M, female 25M
• Blue & Silver credit card are contributing to 93% of overall transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%

<img width="6000" height="4000" alt="image" src="https://github.com/user-attachments/assets/5140a5c7-b7ec-47c8-ac5a-5e1586764975" />
