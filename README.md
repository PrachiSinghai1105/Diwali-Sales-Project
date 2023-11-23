# Diwali-Sales-Project
Introduction

This Python script analyzes Diwali sales data from a CSV file to gain insights into customer behavior and preferences. 
The script utilizes popular data science libraries such as NumPy, Pandas, Matplotlib, and Seaborn.

Code Explanation

1. Importing Libraries
    import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns

3. Loading Data
   df = pd.read_csv('Diwali Sales Data.csv', encoding='unicode_escape')
The script loads the Diwali sales data from a CSV file into a Pandas DataFrame.

3. Data Cleaning
df.drop(['Status', 'unnamed1'], axis=1, inplace=True)
pd.isnull(df).sum()
df.dropna(inplace=True)
df['Amount'] = df['Amount'].astype('int')
df.rename(columns={'Marital_Status':'Shaadi'})

The code drops unnecessary columns, checks for null values, removes null entries, converts the 'Amount' column to integers,
and attempts to rename the 'Marital_Status' column (though this line doesn't modify the DataFrame).

4. Exploratory Data Analysis (EDA)

Gender Analysis
ax = sns.countplot(x='Gender', data=df)
sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Gender', y='Amount', data=sales_gen)

These sections generate bar charts to visualize the distribution of genders and the total sales for each gender.

Age Analysis

ax = sns.countplot(data=df, x='Age Group', hue='Gender')
sales_age = df.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Age Group', y='Amount', data=sales_age)

State Analysis
sales_state = df.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.barplot(data=sales_state, x='State', y='Orders')
sales_state = df.groupby(['State'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.barplot(data=sales_state, x='State', y='Amount')

These sections explore the distribution of orders and total sales across different states.

Marital Status Analysis

ax = sns.countplot(data=df, x='Marital_Status')
sales_state = df.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(data=sales_state, x='Marital_Status', y='Amount', hue='Gender')

These sections investigate the impact of marital status on sales, with a focus on the gender perspective.

Occupation Analysis

ax = sns.countplot(data=df, x='Occupation')
sales_state = df.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(data=sales_state, x='Occupation', y='Amount')

These sections examine the distribution of sales across different occupations.

Product Category Analysis

ax = sns.countplot(data=df, x='Product_Category')
sales_state = df.groupby(['Product_Category'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.barplot(data=sales_state, x='Product_Category', y='Amount')

These sections analyze the sales distribution across various product categories.


# Conclusion:
# Married women age group 26-35 yrs from UP, Maharashtra, and Karnataka working in IT, Healthcare, and Aviation are more likely to buy products from Food, Clothing, and Electronics category

