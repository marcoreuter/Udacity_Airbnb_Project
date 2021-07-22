# Airbnb Boston and Seattle Analysis

This project uses data from Kaggle for the Airbnb listings in Boston (https://www.kaggle.com/airbnb/boston) and Seattle (https://www.kaggle.com/airbnb/seattle).


It analyses the following questions:

1) Which factors correlate with a high rental price for an object? How well can they predict the rental price?  
2) Can the factors that work in Boston predict prices in Seattle? Can the factors that work in Seattle predict prices in Boston?  
3) How well do the review scores match the NLTK language processing scores?  

Packages used:

numpy
pandas
matplotlib.pyplot
sklearn
seaborn
pyarrow
regressors

File descriptions:

- First Look and Data Cleaning.ipynb: Notebook that takes a first look at the data, cleans it and saves it into a parquet format for later use
- Modelling and Analysis.ipynb: Notebook that conducts the main analysis

- boston_listings.csv, boston_reviews.csv, boston_calendar.csv: Initial raw data for Boston that was downloaded from Kaggle
- boston_listings_cleaned, boston_reviews_cleaned, boston_calendar_cleaned: Cleaned data as an output of the "First Look and Data Cleaning" notebook
- seattle_listings.csv, seattle_reviews.csv, seattle_calendar.csv: Initial raw data for Seattle that was downloaded from Kaggle
- seattle_listings_cleaned, seattle_reviews_cleaned, seattle_calendar_cleaned: Cleaned data as an output of the "First Look and Data Cleaning" notebook

Brief summary:

I start by loading in the raw Kaggle data. For all the data, I make sure the data types are as necessary. I drop several columns from the listings file that I don't believe are necessary for the analysis. Then the files are saved as parquet's for later use. In the main analysis I conduct a LASSO regression of the price of an Airbnb on a variety of factors. For Boston, I identify the following as the most important factors:

1) How many guests the Airbnb accommodates
2) If the Airbnb is a private room

For Seattle, the results are 

1) How many guests the Airbnb accommodates
2) How many bedrooms the Airbnb has

Then, I use the Boston regression to predict Seattle prices and vice-verse. Even though the factors in the regressions overlap somewhat, the predictive power is low.

In a second part, I use the NLTK library to analyze the written comments for an Airbnb. Then I use linear regression to regress an Airbnb's rating onto the NLTK compound score. There is a strong relationship between the two (very low p-value). However, predictive power is not particularly high, possibly as the model lacks flexibility given that it only incorporates one regressor.
