# predicting-CO2-levels

## The Scenario
In this paper, I predict atmospheric CO2 concentrations using data collected at the Mauna Loa Observatory between 1958 and 2017. CO2 levels are expected to increase with time, while also varying seasonally due to the Northern Hemisphere’s yearly vegetation cycle (cite). This is reflected in the dataset obtained from Mauna Loa. According to the following statistical analysis, a polynomial model with a sinusoidal component best fit the model in terms of the increasing levels of CO2 as well as the seasonal oscillations. I used Stan to create the model and make predictions using Stan’s default Hamilton Markov Chain Monte Carlo sampling method.
