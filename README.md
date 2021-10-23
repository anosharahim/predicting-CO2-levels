# Predicting Atmospheric Carbon dioxide Concentrations

## The Scenario
In this paper, I predict atmospheric CO2 concentrations using data collected at the Mauna Loa Observatory between 1958 and 2017. CO2 levels are expected to increase with time, while also varying seasonally due to the Northern Hemisphere’s yearly vegetation cycle (cite). This is reflected in the dataset obtained from Mauna Loa. According to the following statistical analysis, a polynomial model with a sinusoidal component best fit the model in terms of the increasing levels of CO2 as well as the seasonal oscillations. I used Stan to create the model and make predictions using Stan’s default Hamilton Markov Chain Monte Carlo sampling method.

## The Model 
The mathematical model is a normal distribution around the above polynomial with a sinusoidal component with a standard deviation that the Stan model will estimate.

### Model Assumptions
Given current global warming, I assumed that CO2 concentrations will continue to increase, and that they will continue to vary at the current rate and amplitude every 1.25 years. These assumptions translated into the model such that I constrain the parameters to be greater than 0. Moreover, I set my priors for the scaling component and the Baseline CO2 level to be uninformative gaussian around a value that seems appropriate given my belief about what historic CO2 concentration in the atmosphere should be and how the model will scale.

### Parameters
- c1- Scaling Component
The scaling component is the coefficient of the highest order polynomial, which impacts the rate of increase of the dependent variable i.e. CO2 levels.
- c2- Amplitude of Seasonal Oscillation
The amplitude of seasonal oscillation represents the seasonal changes in CO2 levels every 1.25 years.
- c3- Baseline CO2 levels
This parameter represents the CO2 levels at the beginning of the data collection, and would serve as the intercept of the function on the y-axis.
- c4- Gradient
This parameter also represents the increase in CO2
in a linear fashion.
- c7- Noise
This parameter represents the standard deviation of the model, or the expected error in the calculation for CO2 levels.

## Results
The above mathematical model is run using Stan, which uses a kind of Markov Chain Monte Carlo sampling method called Hamiltonian. The overall prediction for atmospheric CO2 levels is that they keep increasing 60 years into the future, and by 2034 the CO2 levels will surpass the 450 ppm, which is dangerously high, as can be seen in Figure 2.

The model converged, yielding a high number of effective samples for model parameters as well as predictions. Moreover, the Rhat value is 1 for the estimates, which is good because it indicates that the Markov chains mixed well and that the estimates are reliable. The confidence intervals for model parameters are narrow, giving a high model accuracy for the parameter estimates (see appendix). In order to check the efficacy of the parameter estimates, I created pair plots (see appendix) and
autocorrelation plots (see appendix) over all parameters. Autocorrelation is very low for all estimates, which means that there are no unexplained relationships between the chains. Similarly, the pair plots show that most parameters are centered around a specific mode, providing strong estimates for each parameter. This model is strong because it fits the observations, has narrow confidence intervals, and the pair plots and autocorrelation plots show the strength of the predictions. However, it is important to note that with the advent to climate change, there might be natural phenomena unexplained by this model especially when projected into the future. For example, the assumption that seasonal variation will remain as it is may not hold if seasonal variation changes as a result of a natural feedback loop between increasing CO2 levels and northern hemisphere vegetation cycles. What can be said with more certainty is that CO2 do not seem to be decreasing by any measure, and that this model should be compared with other models to check for what is the mean prediction for CO2
levels surpassing 450ppm in the future.


## References
Maurais, A., & Krinos, A. (2019). Parameter and uncertainty estimation for a model of atmospheric co2 observations. SIAM Undergraduate Research Online, 12. doi:10.1137/18s017533
