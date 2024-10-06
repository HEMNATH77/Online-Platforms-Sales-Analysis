# Online Platforms Sales Analysis

## Overview

This project involves data analysis and visualization using a dataset containing information about various products, including their ratings, prices, categories, and more. The analysis aims to uncover insights about product ratings across categories, platform performance, and price distributions.

## Dataset

The dataset used in this project is named `test.csv` and contains the following columns:

- `id`: Unique identifier for each product
- `title`: Name of the product
- `Rating`: Average rating of the product
- `Category`: Category to which the product belongs
- `platform`: Platform where the product is available
- `Price`: Price of the product
- `Total Ratings`: Total number of ratings received by the product
- `Total Reviews`: Total number of reviews received by the product
- `star_5f`: Number of 5-star ratings
- `star_4f`: Number of 4-star ratings
- `star_3f`: Number of 3-star ratings
- `fulfilled1`: Indicator for whether the product is fulfilled

## Requirements

Make sure you have the following Python libraries installed:

- pandas
- numpy
- plotly

## Display the Shape of the DataFrame


       df.shape  # (5244, 12)
Explanation: The shape attribute gives the dimensions of the DataFrame, showing the number of rows and columns.

## Display the Columns of the DataFrame


          df.columns
Explanation: This code retrieves the column names of the DataFrame.

## Get Descriptive Statistics

       df.describe()
Explanation: This method provides statistical summaries for numerical columns in the DataFrame, including count, mean, standard deviation, min, and max values.

## Get Information About the DataFrame

      df.info()
Explanation: The info() function displays a concise summary of the DataFrame, including the number of non-null entries and data types for each column.

## Rename Columns for Clarity


    df.rename(columns={'maincateg': 'Category', 'actprice1': 'Price', 'norating1': 'Total Ratings', 'noreviews1': 'Total Reviews'}, inplace=True)
Explanation: This line renames several columns in the DataFrame for better clarity and understanding.

## Drop Unnecessary Columns

     df = df.drop(['star_2f', 'star_1f'], axis=1)
Explanation: This code removes specific columns from the DataFrame that are deemed unnecessary for the analysis.

## Check for Missing Values

    df.isna().sum()
Explanation: This command counts the number of missing values in each column of the DataFrame.

## Drop Rows with Missing Values

      df.dropna()
Explanation: This method removes any rows that contain missing values from the DataFrame.

## Display Data Types

      df.dtypes
Explanation: This code retrieves the data types of each column in the DataFrame, providing insights into the kind of data being analyzed.

## Group by Price and Sum

      df.groupby('Price').sum()
Explanation: This operation groups the DataFrame by the Price column and calculates the sum of all other numeric columns for each price group.

## Group by Rating and Aggregate

     df.groupby('Rating').agg({'Price': 'sum', 'Total Ratings': 'mean'})
Explanation: This line groups the DataFrame by Rating and aggregates the Price column by summing it and the Total Ratings column by averaging it.

##  Sort by Total Ratings in Descending Order

     sorted_df_desc = df.sort_values(by='Total Ratings', ascending=False)
Explanation: This code sorts the DataFrame by the Total Ratings column in descending order, allowing you to see which products have the highest ratings.

## Group by Category and Count

     df.groupby("Category").count()
Explanation: This operation counts the number of entries in each category.

## Group by Category and Sum

     df.groupby("Category").sum()
Explanation: This code aggregates the DataFrame by Category, summing all numeric columns.

## Filtered DataFrames Using AND Condition

      filtered_df_and = df[(df['Price'] > 500) & (df['fulfilled1'] == 0)]
Explanation: This line filters the DataFrame to include only those rows where the Price is greater than 500 and fulfilled1 is equal to 0.

## Filtered DataFrames Using OR Condition

      filtered_df_or = df[(df['Price'] > 500) | (df['fulfilled1'] == 0)]
Explanation: This line filters the DataFrame to include rows where either the Price is greater than 500 or fulfilled1 is equal to 0.

# Data Visualizations

      import plotly.express as px

### Bar chart of Ratings by Category
     fig = px.bar(df, x='Rating', y='Category', color='Category', title='Ratings by Category')
     fig.show()
![output_23_0](https://github.com/user-attachments/assets/ac6e48cf-cd02-431b-a967-20797d53868d)

Explanation: This code uses the plotly.express library to create a bar chart displaying the ratings by category.


### Top Products by Price

    Top_Products = df.groupby('title')['Price'].sum().nlargest(10).reset_index()
    fig = px.bar(Top_Products, x='title', y='Price', color='title', title='Products Prices')
    fig.show()
 ![output_24_0](https://github.com/user-attachments/assets/59d17451-eba6-44ad-8456-d2b06f10d540)
   
### Top Platforms by Total Ratings

      Top_Platforms = df.groupby('platform')['Total Ratings'].sum().nlargest(10).reset_index()
     fig = px.funnel(Top_Platforms, x='Total Ratings', y='platform', title='Platforms Total Ratings')
    fig.show()

 ![output_25_0](https://github.com/user-attachments/assets/7e4a5964-251b-4214-a7bf-26db6dd790ee)
   
### Pie Chart of Fulfilled by Platforms

    fig = px.pie(df, values='fulfilled1', names='platform', title='Sum of Fulfilled By Platforms')
    fig.show()

![output_26_0](https://github.com/user-attachments/assets/829fd107-56b3-44f4-af49-20f54fb80431)
    
### ECDF of Total Ratings by Category

    fig = px.ecdf(df, x='Total Ratings', color="Category")
    fig.show()

![output_27_0](https://github.com/user-attachments/assets/e25779c2-e297-46d5-b3d7-4bc1490e84e4)
    
# Conclusion
This project highlights the essential steps taken to analyze the dataset and visualize the findings effectively. If you have any questions or suggestions, feel free to open an issue or submit a pull request!














