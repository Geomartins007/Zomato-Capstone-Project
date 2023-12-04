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

#2. Checking for missing valoues
[columns for columns in df.columns if df[columns].isnull().sum()>0]

#3. Visualizing null values
sns.heatmap(df.isnull(), yticklabels= False, cbar= True, cmap= 'viridis')

#4. Dropping useless columns
final_df= final_df.drop(['Restaurant ID', 'Address', 'Locality Verbose', 'Longitude', 'Latitude'], axis= 1)

#5. Merging the two datasets
final_df= pd.merge(df, df_country, on= 'Country Code', how= 'left')



# Some Key analyses and visualization

#1. Top 4 countries by orders
plt.pie(x= country_values[:4], labels= country_names[:4], autopct= '%1.2f%%', pctdistance= 0.6)

#2. Top 4 cities by orders
city_names= final_df.City.value_counts().index
city_values= final_df.City.value_counts().values
plt.pie(x= city_values[:4], labels= city_names[:4], autopct= '%1.2f%%')

#3. Customer ratings
ratings= final_df.groupby(['Aggregate rating', 'Rating color', 
                  'Rating text']).size().reset_index().rename(columns= {0:'Rating counts'})

sns.barplot(x= 'Aggregate rating', y= 'Rating counts', hue= 'Rating color', 
            data= ratings, palette= ['blue', 'red', 'orange', 'yellow', 'green', 'green'])

#4. Top customer rating
sns.countplot(x= 'Rating color', data= ratings, palette= ['blue', 'red', 'orange', 'yellow', 'green', 'green'])



# More In-depth analyses

1. Find the countries that have given 0 rating.
country_with_zero_rating= final_df[final_df['Aggregate rating'] == 0].groupby(['Country']).size().reset_index()

2. Country with most 'Average rating'
country_with_average_rating= final_df[final_df['Rating text'] == 'Average'].groupby(['Country']).size().reset_index()

3. Country with most 'Excellent rating'
country_with_excellent_rating= final_df[final_df['Rating text'] == 'Excellent'].groupby(['Country']).size().reset_index()

a= country_with_excellent_rating['Country']
b= y= country_with_excellent_rating[0]

ax= sns.barplot(x= a, y=b)

4. Which countries do have online deliveries?
has_online_deliveries= final_df[final_df['Has Online delivery']== 'Yes'].groupby(['Country']).size().reset_index()

5. Countries and cities that ordering now
country_ordering_now= final_df[final_df['Is delivering now']== 'Yes'].groupby(['Country']).size().reset_index()

6. top 5 Cuisines
top_cuisines= final_df.Cuisines.value_counts()[:5].reset_index()

y_values= top_cuisines['index']
x_values= top_cuisines['Cuisines']

plt.pie(x= x_values, labels= y_values, autopct= '%1.2f%%')

```

---

### Results

The EDA findings are summerized below;

- 1. The maximium transaction records come fro India, US, UK, and Brazil.
- 2. Maximium transaction come from New Delhi City (India).
  3. Not rated has the maximium rating.
  4. Maximum frequency occured within the Orange == [(Average and 2.5 - 3.4)]
  5. Minimium frequency occured within the blue == [(Not rated and 0)]
  6. The majority of the Zero rating comes from Indian customers.
  7. The minority of the Zero rating comes from UK customers.
  8. India has the highest average rating followed by US.
  9. The lowest average rating comes from Indonesia, UAE, and SA



