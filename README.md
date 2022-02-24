# Box-Office-Mojo-Linear-Regression-Metis

# International Box Office Success: Predicting which films become successful outside the U.S.

## Abstract
This project used data scraped from Box Office Mojo (https://www.boxofficemojo.com/) about 1200 movies that opened between 2016 and 2021 to explore which features best predict a film's international success, as measured by international gross. An initial linear regression model was constructed using 158 features, but the unstable R^2 values across each K-fold in cross validation suggested that the model was overfit due to multicollinearity. Variation Inflation Factor (VIF) calculations were used to pinpoint and drop features affected by strong multicollinearity. After fitting a standard scalar and Lasso regression and iterating over different combinations of features, a model with 12 features was chosen to train and test on the test data. The test data's R^2 was 0.737, which is not far from the R^2 for the training data of 0.743. By far the variable with the highest predictive power was the domestic (U.S.) gross for the film.

## Design
In this scenario, the clients are a collective of filmmakers living in Kathmandu, Nepal, who have organized a venue to show films. Their primary aim is to showcase films made in and about the Himalayas, but to offset the cost they would like to regularly show a handful of mainstream films that have achieved international success. Since they will only be able to show a subset of all the mainstream films released internationally, the clients want to make sure that the ones they select to screen will be successful. They're looking for investors and as part of their pitch would like to include a model that predicts which movies will be internationally successful. It is not uncommon for there to be a delay of several months between when media is released in the U.S. and when it becomes available in Nepal; thus two of the features selected for inclusion in this model are the domestic gross profit and opening weekend profit for each movie, as that information will already be available when the clients are negotiating for licensing to show the movies in their theatre.

## Data
The Data used for this analysis was scraped from Box Office Mojo (https://www.boxofficemojo.com/) using Requests and BeautifulSoup to extract the data and convert it to Pandas dataframes that could be cleaned and manipulated. In addition to data from the primary statistics page of each of the 1200 movies, I also scraped a list of movies that belong to franchises (https://www.boxofficemojo.com/franchise/) by scraping the links and using each link to open and scrape the names from the page, so that this could be merged with the other dataframe and form an additional Boolean variable.
After scraping, compiling, and cleaning the data, I was left with 1071 observations with 158 columns (including dummy variables). The number of columns decreased as I was modeling.

## Algorithms
1. Train-Test-Split to separate the data to experiment on
2. Linear Regression to assess the initial fit
3. Cross-Validation to check for overfitting
4. VIF calculations to eliminate variables with strong multicollinearity
5. Lasso Regression to scale and regularize the variables

## Tools
1. Requests and BeautifulSoup -- Scraping and parsing HTML from Box Office Mojo
2. Pandas -- Exploring, manipulating, aggregating, and merging dataframes, as well as feature engineering like generating binary dummies to encode categorical data
3. Numpy and Scikit-learn -- Fitting linear regression models, splitting data into train and test sets, executing cross validations, VIF calculations, scaling, and fitting Lasso regression
4. Seaborn and matplotlib -- Pair plots, plotting predicted vs. actual target values
5. Statsmodels -- Generating initial R^2 and coefficients

## Communication
[Metis_Linear_Regression_and_Web_Scraping_Danielle_Ronkos.pdf](https://github.com/dr-dronkos/Box-Office-Mojo-Linear-Regression-Metis/files/8128831/Metis_Linear_Regression_and_Web_Scraping_Danielle_Ronkos.pdf)

