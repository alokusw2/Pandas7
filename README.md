# Pandas7

1 Problem 1 : Immediate Food Delivery I ( https://leetcode.com/problems/immediate-food-delivery-i/ )

-----------------------------------------------

 the customer's preferred delivery date is the same as the order date, then the order is called immediate; otherwise, it is called scheduled.

Write a solution to find the percentage of immediate orders in the table, rounded to 2 decimal places.

The result format is in the following example.

 

------------------------------------------------

import pandas as pd

def food_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    immediate_count = (delivery['order_date'] == delivery['customer_pref_delivery_date']).sum()
    total_count = len(delivery)
    immediate_percentage = round((immediate_count / total_count) * 100, 2)
    return pd.DataFrame({'immediate_percentage': [immediate_percentage]})

------------------------------------------------



2 Problem 2 : Count Salary Categories  ( https://leetcode.com/problems/count-salary-categories/ ) 

-----------------------------------------------
Write a solution to calculate the number of bank accounts for each salary category. The salary categories are:

"Low Salary": All the salaries strictly less than $20000.
"Average Salary": All the salaries in the inclusive range [$20000, $50000].
"High Salary": All the salaries strictly greater than $50000.
The result table must contain all three categories. If there are no accounts in a category, return 0.

Return the result table in any order.

The result format is in the following example.

 


------------------------------------------------
import pandas as pd

def count_salary_categories(accounts: pd.DataFrame) -> pd.DataFrame:
    low = (accounts['income'] < 20000).sum()
    average = ((accounts['income'] >= 20000) & (accounts['income'] <= 50000)).sum()
    high = (accounts['income'] > 50000).sum()
    return pd.DataFrame({
        'category': ['Low Salary', 'Average Salary', 'High Salary'],
        'accounts_count': [low, average, high]
    })


------------------------------------------------

