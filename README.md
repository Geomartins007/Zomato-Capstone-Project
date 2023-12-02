# Zomato-Capstone-Project
Exploratory Data Analysis___Zomato Capstone Project

## Table of Content

 - [About the Company](#about-the-company)
 - [About the dataset](#about-the-dataset)
 - [Key questions](#key-questions)
 - [Tools](#tools)
 - [Data Cleaning](#data-cleaning)
 - [Exploratory Data Analysis EDA](#exploratory-data-analysis-eda)
 - [Data analysis](#data-analysis)
 - [Results](#results)
 - [Limitation](#limitation)
 - [Reference](#reference)

 ---

### About the Company

Zomato is an online food delivery company bringing restaurants and customers together, which not only delivers food but also provides information about restaurants, menus, and user reviews.
The boom in ecommerce is directly influenced by online delivery services.
Zomato is the pioneer in online food delivery service in many countries, which has provided a major advantage in market share.

 ---

### About the dataset
Zomato dataset is real time data set which gives information about restraunts , its cuisins , locality , ratings etc.
The data is taken from url: https://drive.google.com/file/d/1FSa_x3COvCoMODa44qXufO9CQb3ydqKw/view

 ---

### Key questions

- Top Cuisines that ordered
- Top countries and cities using Zomato
- Rating and Country
- Countries and cities with the highest rating
- Countries and their currencies
- What could have resulted to the results?
- Suggestions for Zomato company

 ---

### Tools

- Python
  - Pandas: Data cleaning, Exploratory data analysis (EDA)

  - Seaborn - Data visualization

  - Matplotlib - Data visualization

  - MS PowerPoint - Report preparation

---

### Data Cleaning

In the initial data preparion phase, the following tasks were carried out:

1. Loading dataset/inspections.
     - Info
     - Describe
2. Handling missing/null values.
   - Filling NaN with mode of the class.
   - Droping irrelevant classes.
   - Renaming classes.
 
---

### Data analysis

``` python

#1. Checking null values
train_data.isnull().sum()

OR

#2. Another way to check for missing valoues
[columns for columns in df.columns if df[columns].isnull().sum()>0]

#3. Visualizing null values
sns.heatmap(df.isnull(), yticklabels= False, cbar= True, cmap= 'viridis')


```
