# Airbnb Boston and Seattle Analysis



Business Understanding: 
I analyse the following questions:
1) Which factors correlate with a high rental price for an object? How well can they predict the rental price?  
2) Can the factors that work in Boston predict prices in Seattle? Can the factors that work in Seattle predict prices in Boston?  
3) How well do the review scores match the NLTK language processing scores? 

Data Understanding:
The raw data is taken from Kaggle. The Airbnb listings in Boston (https://www.kaggle.com/airbnb/boston) and Seattle (https://www.kaggle.com/airbnb/seattle). Each dataset contains three separate .csv files.

- Listings.csv: contains information about the listing itself
- Reviews.csv: contains written reviews for a listing
- Calendar.csv: contains data on the availability of a listing throughout the year

Data Preparation: 
For all the data, I make sure the data types are as necessary. I drop several columns from the listings file that I don't believe are necessary for the analysis. Then the files are saved as parquet's for later use.

Modeling:
In the main analysis I conduct a LASSO regression of the price of an Airbnb on a variety of factors. Then, I use the Boston regression to predict Seattle prices and vice-verse. In a second part, I use the NLTK library to analyze the written comments for an Airbnb. Then I use linear regression to regress an Airbnb's rating onto the NLTK compound score.

Evaluation:
Question 1) Which factors correlate with a high rental price for an object? How well can they predict the rental price?  

For Boston, I identify the following as the most important factors that influence the price:

1) How many guests the Airbnb accommodates
2) If the Airbnb is a private room

r2score on training data: 0.23
r2score on testing data: 0.18

For Seattle, the most important factors that influence the price are: 

1) How many guests the Airbnb accommodates
2) How many bedrooms the Airbnb has

r2score on training data: 0.34
r2score on testing data: 0.36

Question 2) Can the factors that work in Boston predict prices in Seattle? Can the factors that work in Seattle predict prices in Boston?  

Using the Boston model to predict Seattle prices and vice-verse, even though the factors in the regressions overlap somewhat, the predictive power is low.

Boston predicting Seattle:

r2score: 0.16

Seattle predicting Boston:

r2score: 0.06

Question 3) How well do the review scores match the NLTK language processing scores? 
 
There is a strong relationship between the two. t-values of the regressions are 26 and 29, corresponding to essentially 0 p-values. However, predictive power is not particularly high (r2score boston: 0.23, r2score seattle: 0.17). Possibly as the model lacks flexibility given that it only incorporates one regressor.





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

