# COVID-19 Web Data Predictor

## Objective

At the onset of the COVID-19 pandemic, Northwell Health, one of the largest health systems in the New York metropolitian area created a project designed to predictt the number of COVID infection cases on a daily basis [^1]. The project, which is available on GitHub, is called the [covid-web-data-predictor](https://github.com/northwell-health/covid-web-data-predictor) and was able to achieve 70% acccuracy on training data. The project methodology and results were released with the hope that it would assist other hospital systems to detect the daily cases of COVID.

Some of the shortcomings of the project were that that it is impossible to reproduce since the original data was not included in the results of the project, only one model, the `Logistic Regression` model, to predict the number of COVID cases, the project did not go further to demonstrate the predictive nature of the model when faced with new data and the project only calculates the accuracy of the model when there are the accuracy metrics that can help gauge its performance.

This project is meant to create a new approach to predicting COVID-19 cases while superseding some of the limitations of the shortcomings of the Northell Health project.

## Data Set Description

This project uses hospital data from the [New York City OpenData portal](https://data.cityofnewyork.us). The hospital data contains daily counts of `cases`, `hospitalizations` and `deaths` from 2020 to 2025 and is an aggregate of hospitals in the New Yor City Metropolitan area. The data includes a breakdown across all 5 boroughs and also provides a daily average for each of the 3 features.The data is served through [data.gov](https://data.gov) which is a government portal for open data. The features of the hospital data include the following `date_of_interest, CASE_COUNT,    PROBABLE_CASE_COUNT, HOSPITALIZED_COUNT, DEATH_COUNT,CASE_COUNT_7DAY_AVG, ALL_CASE_COUNT_7DAY_AVG, HOSP_COUNT_7DAY_AVG, and DEATH_COUNT_7DAY_AVG.`

Also, it uses web trend data from [Google Trends](https://trends.google.com/trends/). The data exported from Google Trends was exported annually from 2020 to 2025. Google trends automatically aggregates the exported data in weekly intervals that represent the average popularity of the term over the course of that week. The data has been filtered to New York City to match the area of the hospital data. The popularity is returned as a string value that ranges from 0 to 100. However, there are times when it returns a value that is non-numeric, like `"< 1"`. The features of the web data include the following `Week, and COVID-19: (New York NY)` where **COVID-19: (New York)** is the poularity rating.

In the Northwell project, analytics data from their website was used to represent the web data. This included activity on Physician landing pages and COVID-19 information pages. For this project, the broad term of **COVID-19** was used in the Google trends search to generate the web data.

At the time of download, the hospital data contained **2054 entries** of data related to hospitalizations and deaths acrosss all 5 boroughgs of New York City. On the other hand, the web data contains a total of **265 entries**.  Mering the two datasets will result in some data loss. However, since the Google data is an average, weekly, normalized amount of the populartiy of the search term, the data was matched to the equivalent avaerage weekly cases of COVID for cases, hospitalizations and deaths.

## Methods

For uniformity, the popularity rating, found in the trend data, was converted to a numeric value. Any popularity rating that could not be converted to a number is represented as 0. The data was joined to the hospital data by the date.

The data was split into training and test data sets. The numeric popularity rating was normalized along with the weekly averages for the number of cases, hospitalizations and deaths.

The data is used to train multiple models. The results are evaluated comapring the **RMSE (Root Mean Square Error)**. The RMSE is the average error, or distance, between the regression line created by the predictions and the actual data. The model with the smallest error represents the model with the best prediction.


## Risks/Concerns

Although there is no likelihood of PII data being exposed in this dataset, the data is broken down by New York City borough and could be used to identify communities that are more at risk for increased cases of COVID. As a result, this could inadvertently be used to discriminate against certain communities.

This should not be used as an exact measure of how COVID will spread. Google specifically indicates that their data is not a poll and it is a randomly chosen count of 100 searches and is a normalized count of the search term at that time and for a specific region [^2]

Care must be taken if adapting this method for working with other disease outbreaks. Different methods of spreading, incubation period and speed of propagation could change the results.

## References
[^1]: Northwell Healths (2025, December 15) Covid Web Data Predictor, GitHub, https://github.com/northwell-health/covid-web-data-predictor

[^2]: Google News Initiative (2025, December 18) Basics of Google Trends, Google, https://newsinitiative.withgoogle.com/resources/trainings/basics-of-google-trends/