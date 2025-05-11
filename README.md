# week-7.py
# Step1. load and inspect data

import pandas as pd

df = pd.read_csv('sales_data.csv')
print(df.head())

# data transformation. Add a new column for revenue.

df['Revenue'] = df['Units_Sold'] * df['Unit_Price']

# group data to calculate total revenue per product.

product_revenue = df.groupby('Product')['Revenue'].sum()
print(product_revenue)

# data visualization 

# bar chart

import matplotlib.pyplot as plt

# Bar chart for revenue per product
product_revenue.plot(kind='bar', title='Total Revenue by Product', color=['skyblue', 'orange'])
plt.xlabel('Product')
plt.ylabel('Revenue ($)')
plt.grid(True)
plt.tight_layout()
plt.show()

# daily sale trends.

daily_sales = df.groupby('Date')['Revenue'].sum()
daily_sales.plot(kind='line', marker='o', title='Daily Revenue')
plt.xlabel('Date')
plt.ylabel('Revenue ($)')
plt.grid(True)
plt.tight_layout()
plt.show()
