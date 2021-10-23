# Predicting Atmospheric Carbon dioxide Concentrations

## The Scenario
In this paper, I predict atmospheric CO2 concentrations using data collected at the Mauna Loa Observatory between 1958 and 2017. CO2 levels are expected to increase with time, while also varying seasonally due to the Northern Hemisphere’s yearly vegetation cycle (cite). This is reflected in the dataset obtained from Mauna Loa. According to the following statistical analysis, a polynomial model with a sinusoidal component best fit the model in terms of the increasing levels of CO2 as well as the seasonal oscillations. I used Stan to create the model and make predictions using Stan’s default Hamilton Markov Chain Monte Carlo sampling method.

## The Model 
The mathematical model is a normal distribution around the above polynomial with a sinusoidal component with a standard deviation that the Stan model will estimate.

### Model Assumptions
Given current global warming, I assumed that CO2 concentrations will continue to increase, and that they will continue to vary at the current rate and amplitude every 1.25 years. These assumptions translated into the model such that I constrain the parameters to be greater than 0. Moreover, I set my priors for the scaling component and the Baseline CO2 level to be uninformative gaussian around a value that seems appropriate given my belief about what historic CO2 concentration in the atmosphere should be and how the model will scale.

### Parameters
1. c1- Scaling Component
The scaling component is the coefficient of the highest order polynomial, which impacts the rate of increase of the dependent variable i.e. CO2 levels.
2. c2- Amplitude of Seasonal Oscillation
The amplitude of seasonal oscillation represents the seasonal changes in CO2 levels every 1.25 years.
3. c3- Baseline CO2 levels
This parameter represents the CO2 levels at the beginning of the data collection, and would serve as the intercept of the function on the y-axis.
4. c4- Gradient
This parameter also represents the increase in CO2
in a linear fashion.
5. c7- Noise
This parameter represents the standard deviation of the model, or the expected error in the calculation for CO2 levels.
