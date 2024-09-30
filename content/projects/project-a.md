---
image: "/images/tree.png"
shortDescription: "A Random Forest Analysis of Integrating Energy and Supply Chain Data for Economic Forecasting"
---

# Overview
This project implements a random forest algorithm to help integrate alternative data into economic indicators for better economic forecasting. In short,alternative data are data sources that can provide addiitional insights into a specific subject matter. 

In this case, the random forest model integrates a series of energy consumption and supply chain data into past GDP to forecast the 2023 GDP as apposed to traditional models that only include past historical values as its features. 

Data sources are accessible directly through the underline links from the findings section.

The full code / notebook can be found at [Github](https://github.com/jackschua/random-forest-econ) 

Alternatively, you can read the [project overview / write-up sample](https://drive.google.com/file/d/16FshyPDVgTMJsSpsONXAiNwIasutDtr0/view?usp=drive_link) that I wrote for fun. 

# Findings 

## Dataset / Features :
The features used consists of data from:
- [<u>The World Bank's World Development Indicators</u>](https://databank.worldbank.org/source/world-development-indicators) : Past GDP from 2000 to 2022.

- [<u>International Energy Agency</u>](https://www.iea.org/data-and-statistics/data-product/world-energy-statistics-and-balances) : Final Energy Consumption for different economic activities (Residential, Transportation, Industry, Commercial & Public Services, and Others).

- [<u>The World Bank's Logistics Performance Index</u>](https://lpi.worldbank.org/) : Supply chain tracking data that scores the competence of trade activies of different countries (Timeliness, Tracking, Customs, Infrastructure, Logistics Quality, Shipments).


<img src="/images/columns.png">

## Random Forest Predictions
80% of the dataset were used to train the Random Forest model and the remaining 20% are used as testing to evaluate the performance of the model. The table below shows the 10 countries involved in the predictions of their 2023 GDP.
<img src="/images/actual.png">

As observed below from the scatter plot, almost all the predictions are close to the actual values except for that one outlier while the residual plot also shows how close the predicted values are to the zero-error red line.
<img src="/images/predict.png">



## Correlation Matrix 
While useful, relying on a Correlation Matrix to identify the significant features is tough for models with large number of features. 
<img src="/images/matrix.png">


## Model Evaluation: Feature Importance
Instead, by using [feature_importances_](https://scikit-learn.org/stable/auto_examples/ensemble/plot_forest_importances.html), we can easily identify the features that have the largest effects on prediction for that model. In this case of alternative data, energy data seems to be most useful in predicting GDP (commericial & public services, industry, residential) while supply chain data does not show the same influence.
<img src="/images/features.png">


## Model Evaluation: How does it make a choice ?
As seen from the tree graph below, each tree starts with a node at the top and gradually makes it way down to the final node based on its conditions. In this image, it starts with estimator = 0 (python starts with 0), the random forest then gradually reaches the final node (to the point where squared_erorr = 0) where it is deemed as the final prediction for that tree.

In this project, our random forest model builds 100 random trees (estimator = 100) with its own conditions and for each iteration of 1 tree, it will make a prediction for the 2023 GDP where the Random Forest finally averages the predictions of all 100 trees to give a final predicted value for the 2023 GDP.

<img src="/images/download.png">

<a href="/images/download.png" download="tree.png">Download this image for better viewing</a>

## Model Evaluation: MSE & Validation Curve
From the validation curve, we can see the initial spike in negative MSE which essentially means that the model is initially underfitted with too few trees (estimators), but it stablizes around the 25th estimators and so. Hence, more trees beyond that does not help much. 
<img src="/images/validation.png">

Additionally seen from the MSE vs No. of Trees graph, we see lower MSE values up to a certain point as the number of trees increases. Beyond that, the improvements then becomes marginal. 

<img src="/images/mse.png">

This basically shows how useful the Random Forests is when it comes to handling models with large number of features. They are practical, robust, and most importantly are not senstive prone to the number of estimators. 







