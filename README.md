# COVID-19 Web Data Predictor

## Background

The COVID-19 Web Predictor is inspired by a similarly named [project](https://github.com/mervinmcdougall/covid-web-data-predictor) developed by [Northwell Health](https://www.northwell.edu/) back in 2020. The goal of that analysis was to predict the highs and lows of COVID cases using web data obtained from Northwell Health's website and daily confirmed infection data collected from its hospitals. The findings of the analysis was made public, but the source data used for conducting the research was not. Consequently, repeating the results has not been possible.

## Goal
The goal of this project is to do the same but making use of more readily available data. The previous project married the daily COVID-19 infection data with activity on the website to help predict COVID cases. Although, web data was identified as originating from Northwell's own website, the source of the infection data was not made clear. It is likely that the data was sourced from the various hospitals that make up the Northwell Health System.

For this project, the web data will be sourced from [Google Trends](https://trends.google.com/trends/) and will be an export of the search term `COVID-19`. The data has also been limited to the city of `New York` for the years `2020` to `2025`. The hospital data is sourced from [data.gov](https://catalog.data.gov/dataset/covid-19-daily-counts-of-cases-hospitalizations-and-deaths) that in turn draws its New York City hospital data from [data.cityofnewyork.us](https://data.cityofnewyork.us/d/rc75-m7u3).

|Data|Source|
|----|-------|
|COVID -19 Hospital Data| https://catalog.data.gov/dataset/covid-19-daily-counts-of-cases-hospitalizations-and-deaths|
|Web Data|https://trends.google.com/trends/explore?cat=45&date=2020-01-01%202025-12-31&geo=US-NY-501&q=%2Fg%2F11j2cc_qll&hl=en-US

## Methodology
The COVID Web Predictor project developed by northwell,utilized **Logistic Regression** which is a linear model for predicting the rate of infection. It was able to achieve approximately **70%** accuracy. This is good as a starting point but cannot be relied upon to plan resource allocation or request more human resources to manage surge in hospitalized infection.

This project will differ from the original COVID project by the following:
1. The analysis will test different models, linear as well as non-linear, to determine which better predicts the rise and fall of confirmed infections. 
2. The analysis will incorporate different methods of analysis such as USING **SHAP** analaysis to determine what are the main features that determine the outcome from the model. Further, rather than making use of accuracy which is a good measure of classification, this will make use of **RMSE (Root Mean Square Error)**. RMSE is a good measure of how closely the model's prediction matches the regression line from training or test data. Consequently, this analysis will treat the problem as a regression problem rather than a classification problem.
3. As stated before, the project will make use of data which is open and readily available.