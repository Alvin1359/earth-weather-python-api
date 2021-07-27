# Python API - Earth's Weather
A repository containing insights as to how a city's latitude and longitude affect its weather.

## Repository Structure
```
Python API Challenge
|__ images/             # contains heatmap with hotel pins for VacationPy
|
|__ output_data/        # contains images of WeatherPy plots and weather_data.csv
|
|
|__ .gitignore          # gitignore file
|
|__ README.md           # readme file
|
|__ VacationPy.ipynb    # contains analysis for VacationPy
|
|__ WeatherPy.ipynb     # contains analysis for WeatherPy
|
|__ api_keys.py         # contains API keys for API's used


```

## API Used:
- OpeanWeatherMap API https://openweathermap.org/api
- Google Places API https://developers.google.com/maps/documentation/places/web-service/overview#Introduction

## API Usage
- Metric units are used in OpenWeatherMap API
- All questions that have imperial units have been converted to metric and rounded to the nearest 0  

|Parameter|Imeperial|Metric| 
|-|-|-| 
|temp|Fahrenheit|Celsius| 
|wind|miles/hour|meter/sec| 
  
## API Keys
- Both API's require an API key to use
- Create an API key for each and paste into _"api_keys.py"_  
  

## Dependencies and Setup
```import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import gmaps
import os
from scipy import stats
from scipy.stats import linregress
from citipy import citipy
import time
```

## Part I - WeatherPy
- Using _np.random_uniform_ to generate a random set of latitude and longitudes across the full possible range
- Using citipy module to find the nearest city name for each coordinate
- Build a query URL and perform an API call to _OpeanWeatherMap API_ to find:
  - City name
  - Country
  - Latitude
  - Longitude
  - Date of call
  - Cloudiness (%)
  - Humidity (%)
  - Max Temperature (°C)
  - Wind Speed (m/s)
- A DataFrame is constructed as below:  
![image](https://user-images.githubusercontent.com/79504423/116266827-6d031a00-a7ae-11eb-8ce9-672be50b0d45.png)  

- The following relationships are plotted  
Temperature (°C) vs. Latitude  
![chart](output_data/city_latitude_vs_max_temperature.png)  
Humidity (%) vs. Latitude  
![chart](output_data/city_latitude_vs_humidity.png)  
Cloudiness (%) vs. Latitude  
![chart](output_data/city_latitude_vs_cloudiness.png)  
Wind Speed (m/s) vs. Latitude  
![chart](output_data/city_latitude_vs_wind_speed.png)  

- A linear regression analysis is completede on the following:  

Northern Hemisphere - Temperature (°C) vs. Latitude!  
![image](https://user-images.githubusercontent.com/79504423/116266929-860bcb00-a7ae-11eb-8d9f-e9d33cf292fd.png)  

Southern Hemisphere - Temperature (°C) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267129-b489a600-a7ae-11eb-8304-16a93d52a6c5.png)  

Northern Hemisphere - Humidity (%) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267155-bc494a80-a7ae-11eb-90e4-9696ac7354e5.png)

Southern Hemisphere - Humidity (%) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267179-c1a69500-a7ae-11eb-9799-993387bcb374.png)

Northern Hemisphere - Cloudiness (%) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267202-c66b4900-a7ae-11eb-821b-da3c96f41523.png)

Southern Hemisphere - Cloudiness (%) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267218-cb2ffd00-a7ae-11eb-896a-1082cf540c55.png)

Northern Hemisphere - Wind Speed (m/s) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267238-d08d4780-a7ae-11eb-8146-7416f881594a.png)

Southern Hemisphere - Wind Speed (m/s) vs. Latitude  
![image](https://user-images.githubusercontent.com/79504423/116267258-d551fb80-a7ae-11eb-921a-e8add867747f.png)

  
  
## Part II - VacationPy
- Using _weather_data.csv_, 
  - Create a heatmap displaying the humidity of each city
  - Narrow down to cities with:
    - Max temperature lower than 27°C and higher than 21°C
    - Wind speed less than 5m/s
    - Cloudiness of 0%
- Construct URL and query Google Place API to find nearest hotel names to narrowed down cities
- On top of the created heatmap, plot hotels with each pin containing _Hotel Name_, _City_, and _Country_.  
![image](Images/hotel_heatmap.jpg)
