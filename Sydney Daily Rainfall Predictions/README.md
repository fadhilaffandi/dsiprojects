# Sydney Daily Rainfall Predictions



## Context 



Human-caused climate change intensifies the heaviest downpours. More than 70% of the planet's surface is water, and as the world warms, more water evaporates from oceans, lakes, and soils. Every 1°F rise also allows the atmosphere to hold 4% more water vapor.


As such the Department of Planning, Industry and Environment(DPIE) of New South Wales is particularly interested in Rainfall statistics, primarily Sydney, as it is one of the more densely populated cities within the state. Predicting the amount of Rainfall is imperative to the planning of the infrastructure of the city. Knowing and predicting Rainfall would aid in the prevention of flooding and the accumulation of stagnant waters. With this information, the DPIE will be able to gauge its drainage capacity and make better decisions.



## Scope

The objective of this project is to be able to predict daily Rainfall for the city of Sydney, to aid the DPIE of NSW to more accurately gauge their current position with Sydney's infrastructures and asssit in their future plans.


## Problem Statement


Accurately predict the daily rainfall amount for  the city of Sydney


## Data Dictionary


    Date — date of observation
    Location — The common name of the location of the weather station
    MinTemp — The minimum temperature in degrees celsius
    MaxTemp — The maximum temperature in degrees celsius
    Rainfall — The amount of rainfall recorded for the day in mm
    Evaporation — The so-called Class A pan evaporation (mm) in the 24 hours to 9am
    Sunshine — The number of hours of bright sunshine in the day.
    WindGustDir — The direction of the strongest wind gust in the 24 hours to midnight
    WindGustSpeed — The speed (km/h) of the strongest wind gust in the 24 hours to midnight
    WindDir9am — Direction of the wind at 9am
    WindDir3pm — Direction of the wind at 3pm
    WindSpeed9am — Wind speed (km/hr) averaged over 10 minutes prior to 9am
    WindSpeed3pm — Wind speed (km/hr) averaged over 10 minutes prior to 3pm
    Humidity9am — Humidity (percent) at 9am
    Humidity3pm — Humidity (percent) at 3pm
    Pressure9am — Atmospheric pressure (hpa) reduced to mean sea level at 9am
    Pressure3pm — Atmospheric pressure (hpa) reduced to mean sea level at 3pm
    Cloud9am — Fraction of sky obscured by cloud at 9am. This is measured in "oktas", which are a unit of eigths. It records how many eigths of the sky are obscured by cloud. A 0 measure indicates completely clear * sky whilst an 8 indicates that it is completely overcast.
    Cloud3pm — Fraction of sky obscured by cloud (in "oktas": eighths) at 3pm. See Cload9am for a description of the values
    Temp9am — Temperature (degrees C) at 9am
    Temp3pm — Temperature (degrees C) at 3pm
    RainToday — Boolean: 1 if precipitation (mm) in the 24 hours to 9am exceeds 1mm, otherwise 0
    RISK_MM — The amount of rain. A kind of measure of the "risk".
    RainTomorrow — The target variable. Did it rain tomorrow?
    
    

## Conclusions and Recommendations


### In Summary:  

Our MSE values for our various models are as follows:

Baseline: **125.6**


SARIMAX: **99.1**


Prophet: **104.2**


GRU: **87.9**



GRU being the best regression estimator for Daily Rainfall.


All our models performed fairly similar with GRU marginally taking the position as best regressor for the prediciton of daily rainfall and as such is our model of choice. However, all of the models were unable to reproduce the large spikes in our test data but managed to capture the increasing/decraesing trends in the days themselves.

There are quite a few caveats for the models above.  
Our SARIMAX model, though it did perform just a little worse than our GRU had a a limitation on seasonality. Here our seasonalities are assumed to recur within a period of less than a year. Yearly seasonalities are unable to be incorporated within our model as it would be assumed to be non seasonal. The seasonality had to be inferred by using a statsmodel decompose and manually imputed in our SARIMAX.  
This limitations is able to be overcome by fb's Prophet and GRU.

fb's prophet infers the seasonality from the data and is able to decompose and present to us the seasonalities and trends of data in different granularities. However both the SARIMAX and and Prophet predicted negative values in its regression models. Obviously in the case of Rainfall, there is no such thing as negative Rainfall and as such requires the conversion of these negative values to 0.  
This didnt seem to be a problem with our GRU.

GRU is a neural network called Gated Recurrent Units. Unlike normal neural networks, it's able to incorporate the time factor by introducing 'memory' to the model. With the interconnection of features and nodes, the correlations and relationships with the production of the target variable is more complex and complete in a sense. It covers aspects that we are unable to impute manually in our usual machine learning methods which are based on prior analyses. As such, even prior to its perusal, it was expected to perform the best out of our options and it did manage to deliver. Even so, despite its complexity, it did not do as well as predicted. This could be attributed to the complexity of weather in itself. The above features may and could have been insufficient factors to accurately predict Rainfall amounts.  

Looking ahead, ways to improve our model would be to incorporate more factors that could influence the Rainfall, such as Wind Speed, which we had to drop due to insufficient data. Also more spatial factors like the weather patterns in other areas/countries may influence our predictions. In other words, the weather situation of a region in close proximity a few days ago may significantly influence our weather today, as opposed to simply our weather itself a few days ago. Even unforseen phenomena such as volcanic eruptions, earthquakes and typhoons in other countries may largely affect not just single predictions but possibly over a period of time as well.

In conclusion, GRU is our model of choice as it has the best MSE score and can be utilised by the DPIE of NSW to predict daily rainfall in Sydney. However, the DPIE should incorporate and consider more factors to further improve this model and possibly utilise it in other regions of the state.