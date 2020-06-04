# Ironhack project 5 Lego linear model regression

![GitHub Logo](https://www.lego.com/cdn/cs/set/assets/blt43d71bdb7a2ee793/pick-a-brick-banner-background-large.jpg?width=1320&height=200&dpr=1)

### Project description
Group project

Here the idea was to create a linear regression model OLS using a dataset to then try to predict values for a specific features in the dataset. We choosed to work with a Lego dataset and try to make a linear regression for the price of the sets.

The Lego datasets was found on a github page, from another user's project.

we first cleaned our dataframe, to make it usable and remove any useless columns or rows. Then we run several steps of linear regression testing, with or without specific features that could change the result. We also tried to check the assumptions of our model to attest its quality.

Steps of the project :
- Data cleaning ; checking nan, type of features, creating the dummies, verifying the normality of our values, handling outliers, etc...
- For every test of models that were made, manual p-hacking (removing one by one the least important features for our model), to predict better the feature of interest, here the price of the sets.
- Checking the R², AIC (model metrics) for the models
- For our main tests of models, checking the  assumptions of linear regression models ; linearity, multicollinearity, autocorrelation, sub-normality, normality
- Predicting price values for our dataset with the best model, and comparison with the actual price values.

### Libraries

- pandas
- datetime
- statsmodel
- add_constant (from statsmodels.tools.tools)
- matplotlib
- seaborn
- boxcox (from scipy.stats)

### Code details

OPEN A JUPYTER INSTANCE TO BE ABLE TO READ THE .ipynb FILE HERE ON GITHUB

- Cleaning steps done mostly with usual methods (checking nan, types, duplicates, drop columns and rows...), details :
  - simplifying theme columns by keeping only the 10 most frequent themes, and gather the rest as Other
  - dummies created for theme, availability, packaging
  - checking normality for numerical features, and modifying them with a boxcox method ; using a log to make values follow normal distribution
  
- linear model creation :
  - split x (features, with and added constant) and y (feature of interest, here the price of lego sets), initiating and fitting the model
  - checking the p-values of every features in the summary of the model, and removing one by one the highest feature, while there still is a p-value above 0.05
  - checking manually the multicollinearity (correlations of features with others), and remove the correlated ones, one at a time and checking the changes everytime

- assumptions checking made with a function provided by the teacher of the bootcamp himself, imported from Assumptions.py

- before comparing predicted values of the model with the actual, it can be better to apply an inverse transformation to the boxcox log that was applied before to the values, that is to say an exponential.

 
### Links

Source page : https://github.com/seankross/lego/blob/master/data-tidy/legosets.csv

Presentation : https://docs.google.com/presentation/d/1oAkaVx9DphL43mfavSeFqCpin5akDWjV-D7Yha8LUak/edit#slide=id.p

