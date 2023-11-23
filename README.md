# Diwali-Sales-Project

# Introduction

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

# Recommendations:

Based on the conclusion that married women in the age group of 26-35 years from Uttar Pradesh (UP), Maharashtra, and Karnataka, working in IT, Healthcare, and Aviation sectors are more likely to buy products from Food, Clothing, and Electronics categories, here are some targeted marketing strategies:

1. Customized Campaigns:
Create targeted marketing campaigns specifically designed for married women in the 26-35 age group.
Tailor advertisements to highlight products from the Food, Clothing, and Electronics categories.

2. Geotargeting:
Concentrate marketing efforts in regions with a high concentration of potential customers, such as UP, Maharashtra, and Karnataka.

3. Online Platforms:
Leverage online platforms, including social media and e-commerce websites, to reach the target audience effectively.
Use targeted online advertising to capture the attention of women in the specified age group and working in specific sectors.

5. Promotional Offers:
Introduce special promotions or discounts on products in the Food, Clothing, and Electronics categories to attract this demographic.

6. Collaborations with Companies:
Partner with companies in the IT, Healthcare, and Aviation sectors to reach employees directly through internal communication channels or employee engagement programs.

7. Content Marketing:
Develop content that resonates with the interests and preferences of the target audience. This could include blog posts, articles, or videos related to lifestyle, career, and product recommendations.

9. In-Store Experience:
If applicable, enhance the in-store experience for this demographic by creating sections or displays that feature products from the identified categories.

9.Customer Loyalty Programs:
Implement loyalty programs to encourage repeat purchases from this specific demographic, offering exclusive benefits or rewards for their continued engagement.

10. Feedback and Engagement:
Seek feedback from the target audience to continually refine marketing strategies and product offerings.
Engage with customers through surveys, social media, or focus groups to understand their evolving preferences.

11. Personalized Communication:
Utilize personalized communication channels, such as email marketing, to send targeted promotions and product recommendations based on individual preferences and purchase history.

12. Social Influencers:
Collaborate with influencers who align with the characteristics and interests of the target demographic to amplify the marketing message.
Remember, the key is to continuously monitor and analyze the effectiveness of these strategies, adjusting them as needed based on customer feedback and market dynamics.
