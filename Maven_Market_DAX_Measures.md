# DAX Measures – Maven Market: Multi-National Sales & Performance Analytics

This document contains the DAX (Data Analysis Expressions) formulas used in the Maven Market: Multi-National Sales & Performance Analytics project.

---

## Total Revenue
**Description:** Multiplies each transaction quantity by the related product retail price and sums the results

```dax
Total Revenue = 
SUMX(Transaction_Data,Transaction_Data[quantity] * RELATED(Products[product_retail_price]))

```

## Total Cost

**Description:** Multiplies each transaction quantity by the related product cost and sums the results

```dax
Total Cost = 
SUMX(Transaction_Data, Transaction_Data[quantity] * RELATED(Products[product_cost]))

```

## Quantity Sold

**Description:** Calculates the total number of units sold by summing quantities from the Transaction_Data table

```dax
Quantity Sold = 
SUM(Transaction_Data[quantity])

```

## Quantity Returned

**Description:** Calculates the total number of units returned by summing quantities from the Return_Data table

```dax
Quantity Returned = 
SUM(Return_Data[quantity])

```

## Unique Product

**Description:** Counts the total number of distinct products based on product name

```dax
Unique Product = 
DISTINCTCOUNT(Products[product_name])

```

## Total Transactions

**Description:** Counts the total number of transaction records in the Transaction_Data table

```dax
Total Transactions = 
COUNTROWS(Transaction_Data)

```

## Total Returns

**Description:** Counts the total number of return records in the Return_Data table

```dax
Total Returns = 
COUNT(Return_Data[quantity])

```

## All Transactions

**Description:** Calculates the total number of transactions across all data, ignoring filters

```dax
All Transactions = 
CALCULATE([Total Transactions],ALL(Transaction_Data))

```

## Last Month Transactions

**Description:** Calculates the total number of transactions from the previous calendar month

```dax
Last Month Transactions = 
CALCULATE([Total Transactions], DATEADD('Calendar'[date],-1,MONTH))

```

## YTD Revenue

**Description:** Calculates year-to-date revenue based on the calendar date context

```dax
YTD Revenue = 
CALCULATE([Total Revenue],DATESYTD('Calendar'[date]))

```

## 60-Day Revenue

**Description:** Calculates total revenue for the last 60 days based on the selected date context

```dax
60-Day Revenue = 
CALCULATE([Total Revenue],DATESINPERIOD('Calendar'[date],MAX('Calendar'[date]),-60,DAY))

```

## Last Month Revenue

**Description:** Calculates total revenue generated in the previous calendar month

```dax
Last Month Revenue = 
CALCULATE([Total Revenue],DATEADD('Calendar'[date],-1,MONTH))

```

## Last Month Returns

**Description:** Calculates the total number of returns recorded in the previous calendar month

```dax
Last Month Returns = 
CALCULATE([Total Returns], DATEADD('Calendar'[date],-1,MONTH))

```

## All Returns

**Description:** Calculates the total number of returns across all data, ignoring filters

```dax
All Returns = 
CALCULATE([Total Returns], ALL(Return_Data))

```

## Last Month Profit

**Description:** Calculates total profit generated in the previous calendar month

```dax
Last Month Profit = 
CALCULATE([Total Profit],DATEADD('Calendar'[date],-1,MONTH))

```

## Weekend Transaction

**Description:** Counts the total number of transactions that occurred on weekends

```dax
Weekend Transaction = 
CALCULATE( 
                        [Total Transactions],'Calendar'[Weekend] = "Y")

```

## % Weekend Transactions

**Description:** Calculates the percentage of total transactions that occurred on weekends

```dax
% Weekend Transactions = 
[Weekend Transaction] / [Total Transactions]

```

## Total Profit

**Description:** Calculates total profit by subtracting total cost from total revenue

```dax
Total Profit = 
[Total Revenue] - [Total Cost]

```

## Profit Margin

**Description:** Calculates profit as a percentage of total revenue

```dax
Profit Margin = 
[Total Profit] / [Total Revenue]

```

## Return Rate

**Description:** Calculates the proportion of sold quantity that was returned

```dax
Return Rate = 
[Quantity Returned] / [Quantity Sold]

```

## Revenue Target

**Description:** Sets a revenue target as a 5% increase over the previous month’s revenue

```dax
Revenue Target = 
[Last Month Revenue] * 1.05

```
